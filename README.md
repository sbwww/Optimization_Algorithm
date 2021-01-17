# Func_Opt

Contents: common local optimization and global optimization algorithms.

# Time: 2019.01.05
- **Gradient descent**, **Newton** method, **Conjugate gradient** method(Python + Matlab), finding the extremum point of a space surface(3D)

**Tips**:
- The speed of gradient descent algorithm is slow, the number of iterations is large, and the final result is approximate;
- Newton method uses the second-order Taylor expansion approximation of the function, converging very fast!
- Conjugate gradient method is a **compromise** between gradient descent and Newton method! Having the convergence rage of Newton method and doesn't need the second derivative! 
—— **Recommend**!! 

# Time: 2019.01.06
- **Damping Newton** method(Python + Matlab): Damped_Newton.m / python_Damped_Newton.py

# Time: 2019.01.07
- **Monte-Carlo** global optimal algorithm(Python + Matlab): Monte_Carlo.m / python_Monte_Carlo.py

# Time: 2019.01.08
- **Monte-Carlo** for *Schaffer* and *Rastrigin* functions(Matlab): Monte_Carlo 
- **Simulated-annealing** global optimal algorithm(Matlab) + Simulated-annealing for *Schaffer* and *Rastrigin* functions(Matlab): Simulated_Annealing
- **Particle-swarm** optimization global algorithm(Matlab) + Particle-swarm for *Schaffer* and *Rastrigin* functions(Matlab): PSO
- Combining MC/SA/PSO with Gradient descent to conduct fine research(Global optimal + Local optimal)
  
**Monte-Carlo(MC)**: Choose the best one based on a large number of samples. For example, There are 1000 apples in a basket, and you take one out at random every time. Then, you take another one out, comparing it with the previous one and keep the bigger one. Follow this loop. The more times you sample, the more likely you are able to pick the largest apple! But unless you take out all 1,000 apples, you never know for sure if the one you're keeping is the biggest one. You know, even if you've got 999 of them, the last one still has the possibility to be the biggest apple! **Advantage**: As long as there is a sufficient number of sampling times, we can certainly get a good result, which means that the algorithm must converge. **Disadvantage**: need a lot of sampling!

**Simulated-annealing(SA)**: This algorithem gradually knows what its goal is! And it keeps moving toward a clearer goal, less and less distracted by temptation. For example,  in order to find out the highest mountain on earth, a rabbit doesn't have the right strategy at the beginning. So it jumps at random for a long time. During the trying time, it may go up to high places, step into flat ground or gully. But as the time passes by, this rabbit wakes up and jumps directly to the highest destination, and finally reaches Mount Everest. **Advantage**: The global optimal solution can be found under the finite number of iterations. **Disadvantage**: For some very complex functions, such as having many local extremum points, if the initial value is not found well, it is very likely that the global optimal solution cannot be found eventually.

**Particle-swarm optimization(PSO)**: Information is shared! Search as a team! Team members share information and make progress together to avoid individuals have shortsightedness and lack of global consciousness. For example, just like in Go Game, focusing only on one corner of the battle does not necessarily lead to the final victory. You should look at the whole board and think of all the pieces as a team. **Advantage**: Better than SA, and can be computed in parallel. —— **Recommend**!! 

**Tips**:
- In complex functions(many minimum traps), such as the *Schaffer* function, MC and PSO have good results, but SA is easy to be caught in traps. 
- PSO has faster computing speed than MC, and has good parallelization characteristics! Easy to change it to a parallel program.
- If the actual function is not too complicated (unlike Schaffer), PSO is a good and economical choice!
- MC works for any problem! Yes, it can find out global optimality for any complex functions as long as doing enough sampling(it is easy to conclude from the idea of this method)!

# Time: 2019.01.09 
- **Ant-colony optimization** algorithm for ordinary binary functions, *Schaffer* and *Rastrigin* functions(Matlab): AG    
- Dealing with complex functions like *Rastrigin*, the AG algorithm uses the 'automatic recheck' mechanism and the gradient descent method to conduct accurate search to ensure that the current model can find the minimum point in the end

**Ant-colony optimization(ACO)**: Like PSO, the ACO also relys on the strength of the teamwork to find the final target! What's special about the ACO is that its 'pheromones evaporate', this concept is unique!

**Tips**:
- When a problem/function is more complex(many local extreme traps), the local minimum points, which are very close to the global optimal point, are the most confusing! SA, PSO, ACO are all likely to fall into these traps, and this problem cannot be solved easily just by adjusting superparameters. The only way to get out of this trap in the current model is to go back and run the program again! Therefore, the choice of the initial value/location/point is very critical!!

---

# 优化算法

内容：常见全局最优、局部最优算法合集 + 思路总结

# 时间：2019.01.05
- 梯度下降、牛顿法、共轭梯度法等matlab和python程序, 求一个空间曲面(3维)的极值点

**注意**：
- 梯度下降算法速度较慢、迭代次数较大，并且最后的结果是近似值；
- 牛顿法利用函数的二阶泰勒展开近似，可以一步到位（收敛很快）！并且结果的精度很高！缺点是需要用到海森矩阵，即函数的二阶导！
- 共轭梯度法是介于梯度下降和牛顿法之间的折中方法，既有牛顿法的收敛速度，又不需要用到函数的二阶导！推荐这种方法！

# 时间：2019.01.06
- 新增“阻尼牛顿法”的matlab和python程序；文件名：Damped_Newton.m / python_Damped_Newton.py 

# 时间：2019.01.07
- 新增“蒙特卡洛全局最优”的matlab和python程序；文件名：Monte_Carlo.m / python_Monte_Carlo.py

# 时间：2019.01.08
- 新增“蒙特卡洛全局最优”算法针对Schaffer函数和Rastrigin函数的matlab程序;  文件名：Monte_Carlo       
- 新增“模拟退火法全局最优”算法的matlab程序，以及其针对Schaffer函数和Rastrigin函数的matlab程序;  文件名：Simulated_Annealing
- 新增“粒子群全局最优”算法的matlab程序，以及其针对Schaffer函数和Rastrigin函数的matlab程序;   文件名：PSO        
- 蒙特卡洛、模拟退火、粒子群全局最优 + 梯度下降精确搜索 的matlab程序(全局搜索 + 精确搜索)。

**蒙特卡洛核心思想**：大量随机抽样下的比对，最后结果就是在当前抽样数量下筛选出的一定是最想要的那个结果。举例：假如篮子里有1000个苹果(你定的测试集)，让你每次闭着眼睛找一个最大的，可以不限制挑选次数；于是，你可以闭着眼随机拿了一个，然后再随机拿一个与第一个比，留下大的；再随机拿一个，与前次留下的比较，又可以留下大的；循环往复这样：拿的次数越多，挑出最大苹果的可能性也就越大!但除非你把1000个苹果都挑一遍，否则你无法肯定最终挑出来的就是最大的一个。如果有10000个苹果的话，继续如此说不定就能找到更大的！       

**模拟退火核心思想**：“渐渐”清楚自己的目标是什么！并不断朝“越发”明确的目标迈进，“越来越”不被诱惑干扰。举例：为了找出地球上最高的山，一只兔子在开始并没有合适的策略，它随机地跳了很长时间！在这期间，它可能走向高处，也可能踏入平地或沟壑。但是，随着时间的流逝，它“渐渐清醒”! 并“直直地”朝着最高的方向跳去，最后就到达了珠穆朗玛峰。        

**粒子群核心思想**：信息的社会共享，以一个团队的形式来搜索！团队里成员信息共享，共同进步；避免一个人工作时出现目光短浅，没有全局意识。举例：就像下围棋，只专注于一个角落的战斗不一定能获取最终的胜利，只有放眼全局，把所有己方的棋子都盘活，相互间彼此帮助，才能获得最后胜利。    

**注意**：
- 在复杂函数处理中(很多极小值陷阱)，例如Schaffer函数，蒙特卡洛和粒子群有很好的效果，但模拟退火很容易受骗走不出陷阱！    
- 粒子群比蒙特卡洛有更快的运算速度，并且有很好的并行化特征！便于其改成成并行化程序。      
- 如果实战中的函数不是太过复杂(不像Schaffer)，用粒子群(群体数量多一些)是很好、很经济的选择！     
- 蒙特卡洛适用于任何问题！没错，是任何复杂函数都可以找到全局最优(从该方法的思想中很容易得出此结论)！

# 时间：2019.01.09    
- 更新7：新增“蚁群全局最优”算法针对普通二元函数最大值、Schaffer函数和Rastrigin函数最小值的matlab程序; 文件名：AG    
- 更新8：AG算法在处理具有高迷惑性Rastrigin函数时，采用“自动重检”机制并用梯度下降法辅助进行精确搜索来保证当前模型最终一定可找到最小值点。     

**蚁群算法核心思想**：和粒子群算法有些相似，都是靠团队的力量共同去找目标！蚁群算法中特殊的是它的"信息素"挥发! 这个效果是其他算法中没有的！    

**注意**：
- 当一个问题/函数较为复杂时(有很多局部极值陷阱)，往往离全局最优“较邻近”的局部极小值点们最具有迷惑性！模拟退火、粒子群、蚁群这三种算法都有可能出现走不出这“最后一关”的情况！这是调参数所不能解决的问题了！唯一可以保证在当前模型下走出这样的陷阱的办法就是重新走。总结：“行百里者半九十”，最后的路最难走。
