## 1. Description of the implementation
The solution is based on the ddpg-bipedal code provided in the [github repository](https://github.com/udacity/deep-reinforcement-learning/tree/master/ddpg-bipedal). The main difference is that, instead of using the OUNoise class, I have added some dropout layers to the actor and critic networks. I did not have time to compare each other, but it seems to work in a similar way.

These layers usually work very well with Deep Learning Networks. They remove information and makes the network more robust.

 In this case, I could not get the network to converge using the OUNoise generator, but adding the dropout layers, the network converged faster than just the network without them.

 ## 2. Learning algorithm
There are no differences with the basic DDPG algorith. The only modification are the Dropout layers.

 The initial idea was testing a basic DDPG algorithm as provided and see how it was going.

After playing with the number of layers and number of units on each layer, I could not make the nework to converge to a solution.

The problem was that I was reusing the max_t parameter that limits the number of steps spent on each episode, to avoid an infinite loop.

The limit was set to a lower value, specific for the bipedal scenario, but was limiting the maximum score that could be obtained in this one.

After changing the parameter to a larger value, it took longer to train, but with higher scores, because in this scenario the score depends on the time that the network can follow the target goal.


 ## 3. Plot of rewards
The average score plot, reveals that the agent has a good learning rate, and reaches the 30 average score quite fast:

![](plot.png)

In this case it achieved the 13 average score in 344 episodes.

## 4.Ideas for Future Work
At least the recommended alternative algorithms (A3C and GAE).
In the case of this implementation, I would explore the OUNoise module, that could not get working. Also, the limit on max_t may be relaxed and see how could work.
There is another issue that I could not solve. This problem takes a lot to train and converge. Even when testing on the Udacity workspace that uses a GPU or in my local computer that does not use a GPU, the train time is similar. I am not sure where the problem is, but definitely seems a good point to improve. 
