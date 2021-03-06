# Selected Algorithm

## :memo: List of Contents
* [정렬 알고리즘이란?](#정렬-알고리즘이란?)
* [선택정렬 알고리즘](#선택정렬-알고리즘)
  * 특징
  * Source
* [퀵정렬 알고리즘](#퀵정렬-알고리즘)
  * 특징
  * Source
* [병합정렬 알고리즘](#병합정렬-알고리즘)
  * 특징
  * Source


## 정렬 알고리즘이란?
-  정렬이란? 순서 없이 배열된 자료들을 값 또는 순서에 따라 재 배열하는 것을 말합니다. 자료를 정렬하는 데 사용하는 자료의 값을 키(Key)라고 합니다. 예를 들면, 파일 크기, 수정 날짜, 이름 등이 있습니다. 또 정렬 순서는 오름차순(ASC)과 내림차순(DESC)가 있습니다.

- 많은 정렬 알고리즘 중에 하나를 선택하는 기준으로는 1) 효율성과 2) 안전성이 있습니다. 
- 1) 효율성은 얼마만큼 빠르게 정렬하는 가를 말합니다. 보통 연산 횟수로 계산되는데 정렬 알고리즘은 값을 비교하는 연산과 자료의 위치를 변경하는 이동 연산으로 구성됩니다.

<div align=center> 

![bigO](https://upload.wikimedia.org/wikipedia/commons/thumb/7/7e/Comparison_computational_complexity.svg/512px-Comparison_computational_complexity.svg.png)

</div>

- 2) 안정성은 키 값이 같은 자료들이 입력한 순서를 그대로 정렬하는가를 말합니다. 기존에 정렬한 내용이 유지되는지를 확인하면 됩니다. 먼저 정렬된 내용이 유지되지 않는다면 불안정 정렬입니다.

![](/assets/images/algorithm/sorted_1.png)

[뒤로](https://github.com/bugkingK/Welcome-To-My-Github/blob/master/Algorithm/README.md)/[위로](#selected-algorithm)

</br></br></br>

### 선택정렬 알고리즘
- 선택정렬 알고리즘이란? 정렬되지 않은 전체 자료 중에서 해당 위치에 맞는 자료를 선택하여 위치를 교환하는 알고리즘입니다. 글로는 이해가 잘 안되지만 그림으론 굉장히 간단한 알고리즘입니다.

![](/assets/images/algorithm/sorted_2.png)

: {80, 75, 10, 60, 15, 49, 12, 25}라는 배열이 있다면 전체를 한 번 검색한 후 가장 작은 값을 첫 번째 인덱스와 위치교환합니다.

![](/assets/images/algorithm/sorted_3.png)

: 다음으로 정렬 전인 배열 중 가장 작은 값을 찾고 두 번째 인덱스와 위치교환을 합니다. 이와 같은 방법으로 마지막 인덱스 전까지 반복합니다.

![](/assets/images/algorithm/sorted_4.png)

: 마지막 인덱스는 가장 큰 값이 되므로 그대로 두면 됩니다.

 - 실행결과 (출처 : 나무위키 정렬알고리즘)
 <div align=center>
  
 ![출처 나무위키](http://upload.wikimedia.org/wikipedia/commons/b/b0/Selection_sort_animation.gif)
 
 </div>
 
 [Source-Swift](/Algorithm/source/sorted/selected.swift)

### 선택알고리즘의 특징
- 이 알고리즘은 1) 이동하는 자료를 선택하고 2) 교환하는 연산 2가지로 구성되어 있습니다. 또 선택과 교환의 갯수대로 n번만큼 루프문을 돌려야하므로 빅오표기법으론 O((n-1) + (n-2) + ... + 3 + 2 + 1) = O(n(n-1) / 2) = O(n^2)이 됩니다. 또 자료 교환시 3번의 이동연산을 포함하기에 O(3(n-1)) = O(n)이 됩니다. 따라서 O(n^2 + n) = O(n^2)이 되고 이는 효율성이 낮은 알고리즘입니다. 또 자료의 교환이 계속되어 정렬의 안전성을 유지할 수 없습니다.

- 알고리즘들 중에 사람의 정렬 방법과 가장 많이 닮은 알고리즘입니다.

- 효율성 : O(n^2) , 안정성 : 유지불가함.

[뒤로](https://github.com/bugkingK/Welcome-My-Github)/[위로](#selected-algorithm)

</br></br></br>

### 퀵정렬 알고리즘
 - 퀵 정렬 알고리즘이란? 중심 값(피봇: Pivot)을 기준으로 두 자료의 키 값을 비교하여 위치를 교환하는 방법입니다.
 
 ![](/assets/images/algorithm/sorted_5.png)

 : 먼저 오름차순 정렬을 기준으로 left는 피봇보다 작은 값이, right는 큰 값이 와야합니다.
 
 ![](/assets/images/algorithm/sorted_6.png)
 
 : 피봇보다 작고, 큰 값을 찾았다면 두 값을 위치교환합니다. 교환 완료 시 left는 오른쪽으로, right는 왼쪽으로 이동하여 두 left와 right가 같은 것을 가리킬 때까지 반복합니다. 
 
 ![](/assets/images/algorithm/sorted_7.png)
 
 : 같은 장소를 가리킨다면 그 곳과 피봇을 위치교환합니다.
 
 ![](/assets/images/algorithm/sorted_8.png)
 
 : 피봇 기준으로 왼쪽은 피봇보다 작은 값이 오른쪽은 큰 값이 위치하게 됩니다. 마지막으로 작은 값 배열과 큰 값 배열 각각 같은 방식으로 퀵 정렬을 실행하면 정렬이 완료됩니다. 단 배열의 원소 갯수가 1이하라면 정렬할 필요가 없습니다.

- 실행결과 (출처 : 나무위키 정렬알고리즘)

![나무위키](http://upload.wikimedia.org/wikipedia/commons/6/6a/Sorting_quicksort_anim.gif)


[Source-Swift](/Algorithm/source/sorted/quick.swift) / [Source-fix-Swift](/Algorithm/source/sorted/quick-fix.swift)

### 퀵정렬 알고리즘의 특징
 - 피봇을 기준으로 2개의 부분집합으로 나눠 정렬하므로 n/2, n/4, n/8, ... , n/2^k와 같이 줄어들어 평균 logn의 연산 횟수가 필요합니다. 또 매 정렬마다 n번의 비교가 필요하여 시간복잡도는 평균 O(nlogn)이 됩니다. 하지만 데이터의 분포가 균형적으로 있다면 O(nlogn)이 맞지만 불균형적으로 분포되어 있다면 O(n^2)의 효율을 갖게 됩니다. 또 퀵정렬은 자료의 교환이 계속일어나기에 정렬의 안전성을 유지할 수 없습니다.
 
 - 사실 시간복잡도가 최악인 경우는 퀵 정렬을 사용할 필요가 없어집니다. 이를 해결하기 위해 피봇의 위치를 랜덤으로 정해줍니다. 

 - 효율성 : 평균O(nlogn), 최악(n^2), 안정성 : 유지불가함.

[뒤로](https://github.com/bugkingK/Welcome-To-My-Github/blob/master/Algorithm/README.md)/[위로](#selected-algorithm)

</br></br></br>

### 병합정렬 알고리즘
 - 병합 정렬이란? 기존 자료를 원소의 갯수가 동일한 부분집합으로 분할하고 분할된 각 부분 집합을 병합하면서 정렬 작업을 완성하는 방식으로 정렬합니다. 또 몇 개의 부분집합으로 나누냐에 따라 종류가 나뉘게 되는데, 2개의 정렬된 자료집합을 병합하는 경우 2-way 병합, n개일 땐 n-way 병합입니다. 저는 2-way 병합을 공부했습니다. 작동원리는 다음과 같습니다.
 
 ![](/assets/images/algorithm/sorted_9.png)
 
 : 먼저 하나의 집합을 원소의 개수와 같은 여러 부분 집합으로 분할합니다.
 
 ![](/assets/images/algorithm/sorted_10.png)
 
 : 원소의 집합들을 다시 하나의 집합으로 되돌리며 병합을 실시합니다. 병합 과정은 다음과 같습니다.
 
 ![](/assets/images/algorithm/sorted_11.png)
 
 : 먼저 집합들의 첫 인덱스를 가리키고 가리킨 두 인덱스의 값을 비교합니다. 둘 중 작은 값은 선택되게 됩니다. 선택되면 다음 인덱스를 가리킵니다.
 
 ![](/assets/images/algorithm/sorted_12.png)
 
 : 둘 중 작은 값을 선택합니다. 이와 같은 행동을 반복합니다.
 
[Source-Swift](/Algorithm/source/sorted/merge.swift) 

### 병합 정렬 알고리즘의 특징
 - 기존 자료를 원소의 갯수가 동일한 부분집합으로 분할하고 또 부분집합들을 병합하므로 O(logn)이 됩니다. 병합할 때 모든 원소를 비교하므로 O(nlogn)이 됩니다. 비교할 때 모든 원소를 다 거치므로 최선, 평균, 최악 모두 O(nlogn)이 됩니다. 하지만 추가 메모리공간이 필요하고 이동횟수가 많다는 단점이 있습니다. 배열 대신 연결리스트를 사용하여 이동 대신 연결포인터만 변경하여 성능을 높일 수 있다합니다. 기존의 선택과 퀵 정렬은 교환 기반이라 안전성을 유지하지 못하지만 병합 정렬은 병합을 기반으로 하여 안전성을 유지할 수 있습니다.


[뒤로](https://github.com/bugkingK/Welcome-To-My-Github/blob/master/Algorithm/README.md)/[위로](#selected-algorithm)

