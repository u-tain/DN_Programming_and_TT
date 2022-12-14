## Отчет
### Теоретическая часть
#### Inception V3 
![inceptionv3](https://production-media.paperswithcode.com/methods/inceptionv3onc--oview_vjAbOfw.png)

Inception V3 [1] - сверточная нейронная сеть, особенностью которой является использование специальных Inception-блоков, состоящих из параллельных сверток. Их использование помогает экономить вычислителные ресурсы.

Кроме того в данной сети используется "auxiliary classifer". Это дополнительный выход в сети, помогающий передать полезные градиенты на нижние слои, чтобы сделать их сразу же полезными и улучшить сходимость во время обучения, борясь с проблемой исчезающего градиента.

Inception-блоки:
![block](https://user-images.githubusercontent.com/43996253/209952317-8ca9e728-bc35-4b95-86cd-54fccef0e986.jpg)

#### Оптимизаторы 
Adam [2]-  алгоритм оптимизации в обучении нейронных сетей. Он использует среднее значение вторых моментов градиентов. В частности, алгоритм вычисляет экспоненциальное скользящее среднее градиента и квадратичный градиент, а параметры beta1 и beta2 управляют скоростью затухания скользящих средних. 

Алгоритм:
![1_zfdW5zAyQxge85gA_mFPYg](https://user-images.githubusercontent.com/43996253/209955365-046546b6-47c5-4f20-b36a-38492f060d76.png)

AdaSmooth [3] - также является алгоритмом оптимизации.Это расширение Adagrad и AdaDelta, которое стремится снизить его агрессивную, монотонно снижающуюся скорость обучения. Вместо того, чтобы накапливать все прошлые квадраты градиентов, AdaSmooth ограничивает окно накопленных прошлых градиентов адаптивно выбранным размером.

Алгоритм:
![Снимок](https://user-images.githubusercontent.com/43996253/209955469-2afc7ef9-89b7-4307-b33d-2921c44ea226.PNG)

### Практическая часть
Данная лабораторная имеет две части. Первая часть заключается в реализации сети Inceptionv3 и оптимизатора AdaSmooth с использованием библиотеки Pytorch, а также в произведении тестов и сравнения данной сети с разными оптимизаторами (Adam и AdaSmooth).
- Inception_V3.py - файл с реализацией нейронной сети InceptionV3 
- AdaSmooth.py - файл с реализацией оптимизатора AdaSmooth
- torch.ipynb - файл с обучением и тестами сети InceptionV3 с разными оптимизаторами (Adam и AdaSmooth)

В качестве параметров для обоих оптимизаторов был выбран шаг оптимизатора равный 0.001. Были подгружены предобученные веса, обучение длилось 50 эпох.Оценка результатов производилась с помощью accuracy и f1-score. На приведенных ниже графиках видно, что же примерно на 30й эпохе можно останавливать обучение сети с обоими оптимизаторами. Кроме того, обучение с оптимизатором AdaSmooth было более гладким и смогло достичь лучших результатов.

![gg](https://user-images.githubusercontent.com/43996253/209961364-d9ca8bce-3f43-4684-bdc5-0e440f193f66.png)

Во второй части данной лабораторной было необходимо с использованием библиотеки Numpy реализовать нейронную сетьи процесс ее обучения. Для реализации была выбрана небольшая сеть LeNet5, которую я попыталась обучить на части датасета MNIST, в качестве оптимизатора был выбран Adam.


- numpy.ipynb - файл с реализацией данной части лабораторной

На графиках ниже представлен loss, accuracy, f1-score на train-выборке в течении пяти эпох обучения. Можно сделать вывод, что модель обучается.
![gc](https://user-images.githubusercontent.com/43996253/209982117-063e0b8f-0893-4ed9-bef3-ccb4841899a5.jpg)

### Использованные источники
[1]  https://arxiv.org/abs/1512.00567v3  
[2]  https://arxiv.org/abs/1412.6980  
[3]  https://arxiv.org/abs/2204.00825  
