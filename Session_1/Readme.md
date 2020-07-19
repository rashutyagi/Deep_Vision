# Session-1-Assignment

Submitted by - Rashu Tyagi (Individually)

## Question -1) What are Channels and Kernels?
### Answer.)  I have written a blog explaining both these terms intuitively with images and here is the link 

Sneak peak from the article 
![](https://github.com/rashutyagi/Deep_Vision/blob/master/Session_1/Image_1.PNG)

![](https://github.com/rashutyagi/Deep_Vision/blob/master/Session_1/Image_2.PNG)


[What are kernels and channels in CNN ? ](https://medium.com/@rashutyagi/what-are-channels-and-kernels-in-convolutional-neural-networks-d6b8b60e00d0?source=friends_link&sk=080c46defb4dd9f9e79fde5e90830eb8)

## Question -2) Why should we (nearly) always use 3x3 kernels?
### Answer.) 

Firstly let us see why can't we use a kernel which is of the order n*n where n is even --> the answer to this question is that there is no symmetry in case of kernels with even orders hence we use kernels of the type n*n only where n is an odd number. Also 3*3 has the central axis

Now the question arises that why to use only 3*3 and not 5*5 or 7*7* or 9*9 --> Then the simple answer to that is "EVERY 5*5 KERNEL CAN BE FORMED USING 2 3*3 KERNELS AND EVERY 7*7 KERNEL CAN BE FORMED USING 3 3*3 KERNELS"

Every 3*3 is a 2*2 also see below:

![](https://github.com/rashutyagi/Deep_Vision/blob/master/Session_1/Image_3.jpg)


Now the question might arise up that instead of using 2 3*3 kernels why can't we use a single 5*5 kernel ? --> What happens in 5*5 kernel is that we have 25 parameters(Why? Pick up a pen and paper and try to figure out) while if we consider 2 3*3 kernels then in total we will have 18(9+9) parameters and this difference starts increasing exponentially hence the best suited kernel for most of the cases is 3*3 only.

This is how it looks :

![](https://github.com/rashutyagi/Deep_Vision/blob/master/Session_1/Image_4.png)

And the another important reason is that 3*3 kernels are accelerated in Nividia Graphic Card.

## Question -3.) How many times to we need to perform 3x3 convolutions operations to reach close to 1x1 from 199x199 (type each layer output like 199x199 > 197x197...)

### Answer -> 

199 * 199 -->197 * 197 -->195 * 195 -->193 * 193 -->191 * 191 -->189 * 189 -->187 * 187 -->185 * 185 -->183 * 183 -->181 * 181 -->179 * 179 -->177 * 177 -->175 * 175 -->173 * 173 -->171 * 171 -->169 * 169 -->167 * 167 -->165 * 165 -->163 * 163 -->161 * 161 -->159 * 159 -->157 * 157 -->155 * 155 -->153 * 153 -->151 * 151 -->149 * 149 -->147 * 147 -->145 * 145 -->143 * 143 -->141 * 141 -->139 * 139 -->137 * 137 -->135 * 135 -->133 * 133 -->131 * 131 -->129 * 129 -->127 * 127 -->125 * 125 -->123 * 123 -->121 * 121 -->119 * 119 -->117 * 117 -->115 * 115 -->113 * 113 -->111 * 111 -->109 * 109 -->107 * 107 -->105 * 105 -->103 * 103 -->101 * 101 -->99 * 99 -->97 * 97 -->95 * 95 -->93 * 93 -->91 * 91 -->89 * 89 -->87 * 87 -->85 * 85 -->83 * 83 -->81 * 81 -->79 * 79 -->77 * 77 -->75 * 75 -->73 * 73 -->71 * 71 -->69 * 69 -->67 * 67 -->65 * 65 -->63 * 63 -->61 * 61 -->59 * 59 -->57 * 57 -->55 * 55 -->53 * 53 -->51 * 51 -->49 * 49 -->47 * 47 -->45 * 45 -->43 * 43 -->41 * 41 -->39 * 39 -->37 * 37 -->35 * 35 -->33 * 33 -->31 * 31 -->29 * 29 -->27 * 27 -->25 * 25 -->23 * 23 -->21 * 21 -->19 * 19 -->17 * 17 -->15 * 15 -->13 * 13 -->11 * 11 -->9 * 9 -->7 * 7 -->5 * 5 -->3 * 3 -->1 * 1

## Question -4.) How are kernels initialized? 

### Answer.) ->
  Each and every kernel consist of weights and those weights we always need to initialize randomly but even though we initialize them randomly we need to keep a few things in mind. We should keep a note of two basic problem in the training of a DNN they are vanishing gradient problem and gradient exploding problem both these problems should be kept in mind before initializing the random weights to a kernel. Now our weights should not be very large nor should they be very small. Now how can this be done ? here comes a little bit of statistics . Statistics says that we should select our random values for our kernel weights from a distribution of numbers which has 0 mean and a constant variance (many times taken as 1) If these two things are followed we have observed experimentally that the gradients dont get into a much of vanishing stage nor into much of exploding  stage they are carried well throughout the layers.
  
  There are 2 famous initializations called as Xavier initilizations and He Initialization which also help in faster convergence of the model and preventing from vanishing and exploding gradient problem.






## Question -5) What happens during the training of a DNN?

### Answer.) 

When we randomly initialize the kernel(and how it is done randomly is shown in answer above) values then that thing sounds ofcourse weird because everyone will be getting totally different outcomes for the same model everytime they run. Now what happens for a DNN is training and that is the most time taking process in the entire DNN cycle. What in short happens in training a DNN is that the kernel values which we initialized randomly are now changed slowly based on the output we received using the previous Kernel values and they are changed in such a way that we get accuracy better than before not immediately after it but yes after a couple of running our networks.

And slowly what happens is that for some particular values of our kernel our model stops showing improvement in accuracy any more and there we say that the training is complete now and the kernel values for that accuracy are our final kernel values.

##### In short learning the kernel values or the weights in order to get good accuracy is what we call as training.





