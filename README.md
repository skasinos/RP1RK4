# RP1RK4 solver for the response of a rigid-plastic single-degree-of-freedom block to arbitrary base acceleration excitation

<p align="center">
<b>  User Instructions </b><br>
</p>

<p align="center">
<b> S. Kasinos </b><br>
</p>

<p align="center">
<b> July 21, 2019 </b><br>
</p>


## 1. Introduction

RP1RK4 is a standalone executable program written in C++ that calculates the response of a rigid-plastic single-degree-of-freedom block to an arbitrary base acceleration input via the fourth-order Runge-Kutta formulation. It can be used in standalone mode, or in conjunction with third-party software. It may find application in parametric, stochastic analysis and optimisation, and can assist learning on the subject of structural dynamics.

## 2. System requirements
The program runs on Windows operating system directly from the command prompt, without the requirement to use any other software. 

## 3. Formulation

The following equation is solved [1]:

<p align="center">
<img src="https://latex.codecogs.com/gif.latex?%5Cddot%7Bu%7D%28t%29%3D%20%5Cbegin%7Bcases%7D%200%2C%20%26%20u%2C%5Cdot%7Bu%7D%3D0%5C%5C%20-%20%5Cmu%5C%2Cg%5C%2C%7B%5Crm%7Bsgn%7D%7D%20%5Cleft%28%20%5Cdot%7Bu%7D%28t%29%20%5Cright%29%20-%5Cddot%7B%5Cxi%7D%28t%29%2C%20%26%20%5Ctext%7Botherwise%7D%20%5Cend%7Bcases%7D%20%5C%2C%2C">
</p>

\noindent where ![](https://latex.codecogs.com/gif.latex?u%28t%29) denotes the unidirectional displacement of the oscillator relative to the ground; ![](\ddot{\xi}(t)) is the base acceleration input, in which the overdot denotes differentiation with respect to time; ![](https://latex.codecogs.com/gif.latex?%5Cmu%3Da/g) is the coefficient of sliding friction assuming horizontal contact surface, ![](https://latex.codecogs.com/gif.latex?a) being the system's specific strength (i.e. the level of the external acceleration ![](https://latex.codecogs.com/gif.latex?%5Cddot%7B%5Cxi%7D%28t%29) required for the oscillator to yield), and $g$ is the acceleration due to gravity; ![](https://latex.codecogs.com/gif.latex?%5Crm%7Bsgn%7D%28%5Ccdot%29) denotes the signum function (i.e. ![](https://latex.codecogs.com/gif.latex?%7B%5Crm%7Bsgn%7D%7D%28x%29%3D&plus;1) if ![](https://latex.codecogs.com/gif.latex?x%3E0), ![](https://latex.codecogs.com/gif.latex?%7B%5Crm%7Bsgn%7D%7D%28x%29%3D-1) if ![](https://latex.codecogs.com/gif.latex?x%3C0), and ![](https://latex.codecogs.com/gif.latex?%7B%5Crm%7Bsgn%7D%7D%28x%29%3D0) if ![](https://latex.codecogs.com/gif.latex?x%3D0)).

## 4. Preparing the input file

Prior to running the solver, the user must provide a standard fixed-length .txt input file which must be placed in the same directory as the solver. The first line comprises of five parameters, namely ![](https://latex.codecogs.com/svg.latex?%5Cinline%20n%2C%20%5Comega%2C%20%5Czeta%2C%20a) and ![](https://latex.codecogs.com/svg.latex?%5Cinline%20%5Cpsi), where ![](https://latex.codecogs.com/svg.latex?%5Cinline%20n) is the length of the input acceleration time history array. The remaining lines are written in two-column format, and list the instances of time ![](https://latex.codecogs.com/svg.latex?%5Cinline%20t) and the input acceleration ![](https://latex.codecogs.com/svg.latex?%5Cinline%20%5Cddot%7B%5Cxi%7D%28t%29), respectively. It is noted that the parameters in each line must be separated with double white space. A consistent system of units should be chosen such as the units of ![](https://latex.codecogs.com/svg.latex?%5Cinline%20%5B%7B%5Crm%7Brad%7D%7D/%7B%5Crm%7Bs%7D%7D%5D) for ![](https://latex.codecogs.com/svg.latex?%5Cinline%20%5Comega), and ![](https://latex.codecogs.com/svg.latex?%5Cinline%20%5B%7B%5Crm%7Bm%7D%7D%7B%5Crm%7Bs%7D%7D%5E%7B-2%7D%5D) for ![](https://latex.codecogs.com/svg.latex?%5Cinline%20a) and ![](https://latex.codecogs.com/svg.latex?%5Cinline%20%5Cddot%7B%5Cxi%7D%28t%29).

## 5. Running the solver

The solver **cannot** be executed by double clicking the executable file. To run the solver, start the command prompt and navigate from the current directory to the one where the executable file is located. For example, 

  ```latex
 cd Desktop
  ```
switches the directory on the command prompt. To run the solver then use:

  ```latex
 B1RK4.exe In.txt Out.txt
  ```
  
 which instructs the command prompt to run the solver after reading the input text file In.txt and write the output to Out.txt. It is noted, that this can also be achieved by calling the system command prompt from a third-party software such as MATLAB or PYTHON. 
  
## 6. Output

Upon successful completion of the analysis the output .txt file will be found in the same directory as the solver. This file will contain four columns, namely, time ![](https://latex.codecogs.com/gif.latex?%5Cinline%20t), and the response state variables ![](https://latex.codecogs.com/gif.latex?%5Cinline%20u%28t%29), ![](https://latex.codecogs.com/gif.latex?%5Cinline%20%5Cdot%7Bu%7D%28t%29) and ![](https://latex.codecogs.com/gif.latex?%5Cinline%20z%28t%29), respectively. The user can process this file by a third-party software to plot the results.

## 7. Support

Please contact s.kasinos@gmail.com.

## References

[1] Kasinos, S. [Seismic response analysis of linear and nonlinear secondary structures](https://dspace.lboro.ac.uk/2134/33728). PhD thesis, 2018.

[2] Giaralis, A. and Kougioumtzoglou, I. [A stochastic dynamics approach for response spectrum analysis of bilinear systems using time-dependent equivalent linear properties](http://hdl.handle.net/2429/53408). Proceedings of the 12th International Conference on Applications of Statistics and Probability in Civil Engineering, 2015.


