# rxbrains
rxbrains with brain.js - Neural Network

[ 클라우드 Rx (<a href='https://rxapis.com'>https://rxapis.com</a>) ]에서 제공합니다.


## Table of Contents
- [Rx Brain Node](#rx-brain-node)
  - [Rx Brain Node 설명](#rx-brain-node-설명)
  - [Rx Brain Node Example](#rx-brain-node-예시)
- [Rx Means Algorithm](#rx-means-algorithm)
  - [Rx Means Algorithm 설명](#rx-means-algorithm-설명)
- [Rx Html Grid Searcher](#rx-html-grid-searcher)
  - [Rx Html Grid Searcher 설명](#rx-html-grid-searcher-설명)

## Rx Brain Node
Rx Brain Node는 brain.js (<a href='https://brain.js.org/'>https://brain.js.org/</a>)의 동적 사용에 관한 라이브러리 입니다.    

* 해당 연도 말까지 테스트 가능합니다.

```javascript
const emotions = {
                networks : [
                    {
                        model : 'gladness',
                        version : '0.1',
                    },
                    {
                        model : 'aggro',
                        version : '0.1',
                    },
                    {
                        model : 'dolor',
                        version : '0.1',
                    },
                    {
                        model : 'joy',
                        version : '0.1',
                    },
                ],
            };

const netNode = new RxFramework.RxBrainNodeC(emotions);

```

### 특징
* brain.js의 Neural Networks의 동적사용
* 데이터의 개수와 상관없이 빠른 사용 가능
* 모델별 사용이 용이

### 사용법
#### Rx Brain Node 설명
* new 생성자를 통해 초기 모델 전달
* function getModels : 준비되어 있는 모델 명 호출 
* function addData : (모델 명, 학습 데이터) 준비되어 있는 모델에 학습시킬 데이터 넣기 

* addData는 기존에 있는 데이터 + 다음 호출 때 부르는 데이터로 더해서 학습함 
* 학습에 따르는 기본값들은 동적으로 자동 설정됨. 
* function run : (모델 명, input 데이터) 값을 통한 수행값 리턴
* run은 해당 노드가 준비되어 있을 때 값 리턴, 아직 준비중이면 undefined 리턴


### Rx Brain Node가 지원하는 brain.js Neural Network
* `brain.NeuralNetwork : O`
* `brain.recurrent.RNN : X`
* `brain.recurrent.GRU : X`
* `brain.recurrent.LSTM : X`
* `brain.recurrent.RNNTimeStep : X`
* `brain.recurrent.GRUTimeStep : X`
* `brain.recurrent.LSTMTimeStep : X`


### 예시
#### Rx Brain Node Example
* RX 가위바위보 게임
<img width="1659" alt="스크린샷 2024-09-01 오전 9 19 51" src="https://github.com/user-attachments/assets/93cb4423-51d7-4742-979d-7c2a714d4c1e" />



## Rx Means Algorithm
* 해당 연도 말까지 테스트 가능합니다.

<img width="1659" alt="스크린샷 2024-09-01 오후 12 30 38" src="https://github.com/user-attachments/assets/42900839-771a-4057-8fc5-08ca98756597">
<img width="1659" alt="스크린샷 2024-09-01 오후 12 30 27" src="https://github.com/user-attachments/assets/60303f0a-8cc4-4b7c-ab57-39e0c11eff83">

```javascript

const rx = new RxFramework.RxMeansAL();
rx.SetDistanceWay(true);
rx.SetStaticCentroids(centroids);
rx.SetPoints(points);
const cluster = rx.ExecRxCluster();

```

### 특징
* 다중 차원 좌표값 클러스터링
* (선택) 유클리드 또는 맨해튼 거리 측정법 사용
* 라벨별 사용 용이


### 사용법
#### Rx Means Algorithm 설명

* new 생성자 - 전달 옵션 없음
* function SetDistanceWay : (boolean) true : 유클리드 거리 측정, false : 멘해튼 거리 측정 - default : true
* function SetStaticCentroids : (centroids)

```javascript
// Sample Centroids
// const target = document.body;
const target = document.getElementById('targetDom');
const targetRect = target.getBoundingClientRect();
const targetMinX = targetRect.x;
const targetMaxX = targetRect.x + targetRect.width;
const targetMinY = targetRect.y;
const targetMaxY = targetRect.y + targetRect.height;
const targetMiddle = [ targetMinX + (targetRect.width / 2), targetMinY + (targetRect.height / 2)];

const centroids = [
    { points : [targetMinX, targetMinY] , label : 'topLeft'},
    { points : [targetMiddle[0], targetMinY], label : 'topMiddle'}, 
    { points : [targetMaxX, targetMinY], label : 'topRight'}, 

    { points : [targetMinX, targetMiddle[1]], label : 'middleLeft' }, 
    { points : [targetMiddle[0], targetMiddle[1]], label : 'middleMiddle' }, 
    { points : [targetMaxX, targetMiddle[1]], label : 'middleRight' }, 

    { points : [targetMinX, targetMaxY], label : 'bottomLeft' }, 
    { points : [targetMiddle[0], targetMaxY], label : 'bottomMiddle' }, 
    { points : [targetMaxX, targetMaxY], label : 'bottomRight' }, 
];

```

* function SetPoints : (points) key(points) into Object

```javascript
    const x = Math.round(Math.random() * document.body.offsetWidth);
    const y = Math.round(Math.random() * document.body.offsetHeight);

    // Object into 'points'
    points.push({ points : [x, y], ...etc });

```

* function ExecRxCluster : () 클러스터링. 결과물 반환
* function Clear : () 세팅 데이터 초기화



## Rx Html Grid Searcher
* 해당 연도 말까지 테스트 가능합니다.

```javascript
    const rxGridSearcher = new RxFramework.RxHtmlGridSearcher();
    rxGridSearcher.SearchGrid(document.getElementById('targetDom'));
```

### --
#### Rx Html Grid Searcher 설명

* Rx Means Algorithm을 통한 깊이 탐색 및 그리드 판별
* 홈페이지별 정확도 테스트 중
