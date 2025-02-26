# utl-area-between-curves-with-an-intersection-point-adding-negative-and-positive-areas-plot-sympy
Area between curves with an intersection point adding negative and positive areas plot sympy 
    %let pgm=utl-area-between-curves-with-an-intersection-point-adding-negative-and-positive-areas-plot-sympy;

    Area between curves with an intersection point adding negative and positive areas plot sympy

    github
    https://tinyurl.com/msf55wcf
    https://github.com/rogerjdeangelis/utl-area-between-curves-with-an-intersection-point-adding-negative-and-positive-areas-plot-sympy

    stackoverflow
    https://tinyurl.com/y83rvj2n
    https://stackoverflow.com/questions/79371513/estimating-area-curve-between-two-curves#79371513

          SOLUTIONS

              1 manual solution
              2 python symbolic math
              3 r numerical analysis
              4 related repos
    /*               _     _
     _ __  _ __ ___ | |__ | | ___ _ __ ___
    | `_ \| `__/ _ \| `_ \| |/ _ \ `_ ` _ \
    | |_) | | | (_) | |_) | |  __/ | | | | |
    | .__/|_|  \___/|_.__/|_|\___|_| |_| |_|
    |_|
    */

    /***********************************************************************************8******************************************************/
    /*                                             |                                            |                                             */
    /*        MANUAL COMPUTATIONS                  |     PROCESSES                              |      OUTPUT                                 */
    /*                                             |                                            |                                             */
    /*                                             |                                            |                                             */
    /*                                             |                                            |                                             */
    /*  Consider the two Beta pdfs                 | 1 MANUAL COMPURATION                       |                                             */
    /*                                             |   SEE LEFT PANEL                           |                                             */
    /*    beta(x,3,2) = 12*x**2*(1-x)              | =====================                      | SEE LEFT PANEL                              */
    /*    beta(x,2,2) = 6*x*(1-x)                  |----------------------------------------------------------------------------------------- */
    /*                                             |                                            |                                             */
    /*                                             | 2 PYTHON SYMBOLIC MATH                     |                                             */
    /*                   x**(a-1)*(1-x)**(b-1)     | ======================                     |                                             */
    /*    beta(x,a,b) =  ---------------------     |                                            |                                             */
    /*                      norm(a,b)              |  %utl_pybeginx;                            |  beta1(x.3,2) = 12*x *(1 - x)               */
    /*                                             |  parmcards4;                               |  beta2(x,2,2)  = 6*x*(1 - x)                */
    /*    norm is the constant needed for          |  import sympy as sp                        |                                             */
    /*    the area under x**(a-1)*(1-x)**(b-1)     |  import pandas as pd                       |                              3      2       */
    /*    to equal 1                               |  x = sp.symbols('x')                       |  beta(x,2,2)-beta(x,3,2)=12*x  - 18*x +6*   */
    /*                                             |  beta1_3_2 =x**2*(1-x)*12                  |  Intersection points        = [0, 1/2, 1]   */
    /*    for integer a and b                      |  beta2_2_2 =x*(1-x)*6                      |   /                                         */
    /*                                             |  print("The two beta pdfs")                |   |                          4     3   2    */
    /*    norm= (a-1)! * (b-1)!/ (a+b-1)!          |  sp.pprint(beta1_3_2)                      |   |beta(x,2,2)-beta(x,3,2)=3*x -6*x +3*x    */
    /*                                             |  sp.pprint(beta2_2_2)                      |   |                                         */
    /*                                             |  simpx=sp.expand(beta2_2_2-beta1_3_2)      |  /                                          */
    /* --+--------+--------+--------+--------+---  |  print("beta(x,2,2) - beta(x,3,2)")        |      .5                                     */
    /* |                                        |  |  sp.pprint(simpx)                          |    /                                        */
    /* | TWO BETA PDFS (MANUAL SOLUTION         |  |  intersection_points =  \                  |   |     4      3      2                     */
    /* |                                        |  |    sp.solve(sp.Eq(beta2_2_2,beta1_3_2),x)  |   |  3*x  - 6*x  + 3*x  + c    = 0.1875     */
    /* | f1=beta(3,2) = 12*x**2*(1-x)           |  |  print(intersection_points);               |   |                                         */
    /* | f2=beta(2,2) = 6*x*(1-x)               |  |  flt=float(intersection_points[1])         |  /                                          */
    /* |                                        |  |  area1 = sp.integrate( \                   |   0                                         */
    /* | Finding intersection points f1-f2      |  |    beta2_2_2-beta1_3_2, (x))               |      1                                      */
    /* |                                        |  |  sp.pprint(area1)                          |    /                                        */
    /* | f1-f2 = 0 = 12*x**3 - 18*x**2 + 6*x    |  |  area1e = sp.integrate( \                  |   |     4      3      2                     */
    /* | 0 and 1 are intersection points also   |  |    beta2_2_2-beta1_3_2,(x,0,flt))          |   |  3*x  - 6*x  + 3*x  + c    = -0.1875    */
    /* | simplyfying &  using quadratic formula |  |  sp.pprint(area1e)                         |   |                                         */
    /* | (+3 - sqrt(9 - 8))/4 = 1/2             |  |  area2e = sp.integrate( \                  |  /                                          */
    /* |                                        |  |   beta2_2_2-beta1_3_2, (x, flt,1))         |   .5                                        */
    /* | Intersection points [0,1/2,1]          |  |  sp.pprint(area2e)                         |  total_area                    =  0.375     */
    /* |                                        |  |  tot=area1e+abs(area2e)                    |                                             */
    /* | Integrating 0 to 1/2 '+' area          |  |  print(tot)                                |                                             */
    /* |                                        |  |  ;;;;                                      |                                             */
    /* |     .5                                 |  |  %utl_pyendx;                              |                                             */
    /* |    /                                   |  |------------------------------------------------------------------------------------------*/
    /* | 6 | 2*x**3 - 3*x**2 + x dx             |  |                                            |                                             */
    /* |   /                                    |  | 3 R NUMERICAL ANALYSIS                     |                                             */
    /* |   0                                    |  | ======================                     |                                             */
    /* |                                        |  |                                            |                                             */
    /* | = 6*(2*x**4/4-3*x**3/3+x**2/2)         |  |                                            |                                             */
    /* |                                        |  |   %utl_rbeginx;                            |  > root2                                    */
    /* | = 6*(2/64- 3/24+ 1/8) - 0 = 0.1875     |  |   parmcards4;                              |  [1] 0.5                                    */
    /* |                                        |  |   library(ggplot2)                         |                                             */
    /* |     1                                  |  |   library(dplyr)                           |  > area1<- integrate(betadif                */
    /* |    /                                   |  |   library(stats)                           |  + , 0, root2)$value                        */
    /* | 6 | 2*x**3 - 3*x**2 + x dx             |  |   library(rootSolve)                       |  > area1                                    */
    /* |   /                                    |  |     beta1<-function(x) 6*x*(1-x)           |  [1] -0.1875                                */
    /* |   .5                                   |  |     beta2<-function(x) 12*x**2*(1-x)       |                                             */
    /* |                                        |  |     betadif<-function(x)                   |  > area2<- integrate(betadif                */
    /* | =6*((.5-1+.5)-(2/64- 3/24+ 1/8))=-.1875|  |       12*x**2*(1-x) - 6*x*(1-x)            |  + , root2, 1)$value                        */
    /* |                                        |  |     root2 <- uniroot.all(betadif           |  > area2                                    */
    /* | Tot area between = 2 * .1875 =.375     |  |       ,interval=c(0,1))[2]                 |  [1] 0.1875                                 */
    /* |                                        |  |     root2                                  |                                             */
    /* |0.00     0.27     0.54     0.81     1.08|  |     area1<- integrate(betadif              |  > tot <-abs(area1)+abs(area2)              */
    /* +-+--------+--------+--------+--------+--+ 3|      , 0, root2)$value                     |  > tot                                      */
    /* |                                        |  |     area1                                  |  [1] 0.375                                  */
    /* |  FOR DEMONSTRATION PURPOSE ONLY        |  |     area2<- integrate(betadif              |                                             */
    /* |                                        |  |        , root2, 1)$value                   |                                             */
    /* |      xxxx <- beta(x,3,2)=12*x**2*(1-x) |  |     area2                                  |                                             */
    /* |     xx+++x                             |  |     tot <-abs(area1)+abs(area2)            |                                             */
    /* |     x+++++x  TOTAL AREA BETWEEN= .375  |  |     tot                                    |                                             */
    /* +    xx++++++x ------------------------  + 2|   ;;;;                                     |                                             */
    /* |    x++++++++x                          |  |   %utl_rendx;                              |                                             */
    /* |    x++++++++xx   --<-beta(2,2)-6*(1-x) |  |------------------------------------------------------------------------------------------*/
    /* |   x++++++++++x *----*                  |  |                                            |                                             */
    /* |   x++++++++ **x------**                |  |                                            |                                             */
    /* |   x+++++++**   x------***              |  |                                            |                                             */
    /* |   ++++++**     xx-------**             |  |                                            |                                             */
    /* +  x++++ **       xx--------**           + 1|                                            |                                             */
    /* |  x+++**          x---------**          |  |                                            |                                             */
    /* |   ++**            x---------**         |  |                                            |                                             */
    /* |  x+**              xx--------**        |  |                                            |                                             */
    /* |   **                xx--------**       |  |                                            |                                             */
    /* | x**                  xx--------**      |  |                                            |                                             */
    /* |  *                     xxx------**     |  |                                            |                                             */
    /* + *                         xxx----*     + 0|                                            |                                             */
    /* --+--------+--------+--------+--------+---  |                                            |                                             */
    /* 0.00     0.27     0.54     0.81     1.08    |                                            |                                             */
    /*                  X                          |                                            |                                             */
    /******************************************************************************************************************************************/


    /*                                     _             _       _   _
    / |  _ __ ___   __ _ _ __  _   _  __ _| |  ___  ___ | |_   _| |_(_) ___  _ __
    | | | `_ ` _ \ / _` | `_ \| | | |/ _` | | / __|/ _ \| | | | | __| |/ _ \| `_ \
    | | | | | | | | (_| | | | | |_| | (_| | | \__ \ (_) | | |_| | |_| | (_) | | | |
    |_| |_| |_| |_|\__,_|_| |_|\__,_|\__,_|_| |___/\___/|_|\__,_|\__|_|\___/|_| |_|

    */

     SEE ABOVE


    /*___                _   _                                      _           _ _                        _   _
    |___ \   _ __  _   _| |_| |__   ___  _ __   ___ _   _ _ __ ___ | |__   ___ | (_) ___   _ __ ___   __ _| |_| |__
      __) | | `_ \| | | | __| `_ \ / _ \| `_ \ / __| | | | `_ ` _ \| `_ \ / _ \| | |/ __| | `_ ` _ \ / _` | __| `_ \
     / __/  | |_) | |_| | |_| | | | (_) | | | |\__ \ |_| | | | | | | |_) | (_) | | | (__  | | | | | | (_| | |_| | | |
    |_____| | .__/ \__, |\__|_| |_|\___/|_| |_||___/\__, |_| |_| |_|_.__/ \___/|_|_|\___| |_| |_| |_|\__,_|\__|_| |_|
            |_|    |___/                            |___/
    */

    %utl_pybeginx;
    parmcards4;
    import sympy as sp
    import pandas as pd
    x = sp.symbols('x')
    beta1_3_2 =x**2*(1-x)*12
    beta2_2_2 =x*(1-x)*6
    print("The two beta pdfs")
    sp.pprint(beta1_3_2)
    sp.pprint(beta2_2_2)
    simpx=sp.expand(beta2_2_2-beta1_3_2)
    print("beta(x,2,2) - beta(x,3,2)")
    sp.pprint(simpx)
    intersection_points =  \
      sp.solve(sp.Eq(beta2_2_2,beta1_3_2),x)
    print(intersection_points);
    flt=float(intersection_points[1])
    area1 = sp.integrate( \
      beta2_2_2-beta1_3_2, (x))
    sp.pprint(area1)
    area1e = sp.integrate( \
      beta2_2_2-beta1_3_2,(x,0,flt))
    sp.pprint(area1e)
    area2e = sp.integrate( \
     beta2_2_2-beta1_3_2, (x, flt,1))
    sp.pprint(area2e)
    tot=area1e+abs(area2e)
    print(tot)
    ;;;;
    %utl_pyendx;



    /**************************************************************************************************************************/
    /*                                                                                                                        */
    /*  The following are the two beta pdfs                                                                                   */
    /*                                                                                                                        */
    /*                                   2                                                                                    */
    /*  beta1(x.3,2)                = 12*x *(1 - x)               3 +-+--------+--------+--------+--------+--+ 3              */
    /*                                                              |                                        |                */
    /*  beta2(x,2,2)                = 6*x*(1 - x)                   |  FOR DEMONSTRATION PURPOSE ONLY        |                */
    /*                                                              |                                        |                */
    /*                                  3       2                   |      xxxx <- beta(x,3,2)=12*x**2*(1-x) |                */
    /*  beta(x,2,2) - beta(x,3,2)   = 12*x  - 18*x  + 6*x           |     xx+++x                             |                */
    /*                                                              |     x+++++x                            |                */
    /*  Intersection points         = [0, 1/2, 1]                 2 +    xx++++++x                           + 2              */
    /*                                                              |    x++++++++x                          |                */
    /*   /                                                          |    x++++++++xx   --<-beta(2,2)-6*(1-x) |                */
    /*  |                                4      3      2            |   x+ 0.1875 +x *----*                  |                */
    /*  | beta(x,2,2) - beta(x,3,2) = 3*x  - 6*x  + 3*x  + c        |   x++++++++ **x------**                |                */
    /*  |                                                           |   x+++++++**   x------***              |                */
    /* /                                                            |   ++++++**     xx-------**             |                */
    /*     .5                                                     1 +  x++++ **       xx--------**           + 1              */
    /*   /                                                          |  x+++**          x---------**          |                */
    /*  |     4      3      2                                       |   ++**            x- 0.1875 **         |                */
    /*  |  3*x  - 6*x  + 3*x  + c    = 0.1875                       |  x+**              xx--------**        |                */
    /*  |                                                           |   **                xx--------**       |                */
    /* /                                                            | x**                  xx--------**      |                */
    /*  0                                                           |  *                     xxx------**     |                */
    /*     1                                                      0 + *                         xxx----*     + 0              */
    /*   /                                                          --+--------+--------+--------+--------+---                */
    /*  |     4      3      2                                       0.00     0.27     0.54     0.81     1.08                  */
    /*  |  3*x  - 6*x  + 3*x  + c    = -0.1875                                       X                                        */
    /*  |                                                                                                                     */
    /* /                                                                                                                      */
    /*  .5                                                                                                                    */
    /*                                                                                                                        */
    /* total_area                    =  0.375                                                                                 */
    /*                                                                                                                        */
    /**************************************************************************************************************************/

    /*____                                         _           _                    _           _
    |___ /  _ __   _ __  _   _ _ __ ___   ___ _ __(_) ___ __ _| |  __ _ _ __   __ _| |_   _ ___(_)___
      |_ \ | `__| | `_ \| | | | `_ ` _ \ / _ \ `__| |/ __/ _` | | / _` | `_ \ / _` | | | | / __| / __|
     ___) || |    | | | | |_| | | | | | |  __/ |  | | (_| (_| | || (_| | | | | (_| | | |_| \__ \ \__ \
    |____/ |_|    |_| |_|\__,_|_| |_| |_|\___|_|  |_|\___\__,_|_| \__,_|_| |_|\__,_|_|\__, |___/_|___/
                                                                                       |___/
    */

    %utl_rbeginx;
    parmcards4;
    library(ggplot2)
    library(dplyr)
    library(stats)
    library(rootSolve)
      beta1<-function(x) 6*x*(1-x)
      beta2<-function(x) 12*x**2*(1-x)
      betadif<-function(x)
        12*x**2*(1-x) - 6*x*(1-x)
      root2 <- uniroot.all(betadif
        ,interval=c(0,1))[2]
      root2
      area1<- integrate(betadif
       , 0, root2)$value
      area1
      area2<- integrate(betadif
         , root2, 1)$value
      area2
      tot <-abs(area1)+abs(area2)
      tot
    ;;;;
    %utl_rendx;

    /**************************************************************************************************************************/
    /*                                                                                                                        */
    /* > root2                                                                                                                */
    /* [1] 0.5                                                                                                                */
    /*                                                                                                                        */
    /* > area1<- integrate(betadif                                                                                            */
    /* + , 0, root2)$value                                                                                                    */
    /* > area1                                                                                                                */
    /* [1] -0.1875                                                                                                            */
    /*                                                                                                                        */
    /* > area2<- integrate(betadif                                                                                            */
    /* + , root2, 1)$value                                                                                                    */
    /* > area2                                                                                                                */
    /* [1] 0.1875                                                                                                             */
    /*                                                                                                                        */
    /* > tot <-abs(area1)+abs(area2)                                                                                          */
    /* > tot                                                                                                                  */
    /* [1] 0.375                                                                                                              */
    /*                                                                                                                        */
    /**************************************************************************************************************************/
    /*  _              _         _           _
    | || |    _ __ ___| | ____ _| |_ ___  __| |  _ __ ___ _ __   ___  ___
    | || |_  | `__/ _ \ |/ / _` | __/ _ \/ _` | | `__/ _ \ `_ \ / _ \/ __|
    |__   _| | | |  __/   < (_| | ||  __/ (_| | | | |  __/ |_) | (_) \__ \
       |_|   |_|  \___|_|\_\__,_|\__\___|\__,_| |_|  \___| .__/ \___/|___/
                                                         |_|
    */

    REPO
    ---------------------------------------------------------------------------------------------------------------------------------------
    https://github.com/rogerjdeangelis/utl-r-python-compute-the-area-between-two-curves-AI-sympy-trapezoid

    https://github.com/rogerjdeangelis/utl-calculating-the-cube-root-of-minus-one-with-drop-down-to-python-symbolic-math-sympy
    https://github.com/rogerjdeangelis/utl-distance-between-a-point-and-curve-in-sql-and-wps-pythony-r-sympy
    https://github.com/rogerjdeangelis/utl-fun-with-sympy-infinite-series-and-integrals-to-define-common-functions-and-constants
    https://github.com/rogerjdeangelis/utl-maximum-likelihood-estimate-of--therate-parameter-lamda-of-a-Poisson-distribution-sympy
    https://github.com/rogerjdeangelis/utl-maximum-liklihood-regresssion-wps-python-sympy
    https://github.com/rogerjdeangelis/utl-mle-symbolic-solution-for-mu-and-sigma-of-normal-pdf-using-sympy
    https://github.com/rogerjdeangelis/utl-python-sympy-projection-of-the-intersection-of-two-parabolic-surfaces-onto-the-xy-plane-AI
    https://github.com/rogerjdeangelis/utl-r-python-compute-the-area-between-two-curves-AI-sympy-trapezoid
    https://github.com/rogerjdeangelis/utl-roots-of-a-non-linear-function-using-python-sympy
    https://github.com/rogerjdeangelis/utl-solve-a-system-of-simutaneous-equations-r-python-sympy
    https://github.com/rogerjdeangelis/utl-symbolic-algebraic-simplification-of-a-polynomial-expressions-sympy
    https://github.com/rogerjdeangelis/utl-symbolic-solution-for-the-gradient-of-the-cumulative-bivariate-normal-using-erf-and-sympy
    https://github.com/rogerjdeangelis/utl-symbolically-solve-for-the-mean-and-variance-of-normal-density-using-expected-values-in-SymPy
    https://github.com/rogerjdeangelis/utl-sympy-exact-pdf-and-cdf-for-the-correlation-coefficient-given-bivariate-normals
    https://github.com/rogerjdeangelis/utl-sympy-technique-for-symbolic-integration-of-bivariate-density-function
    https://github.com/rogerjdeangelis/utl-vertical-distance-covered-by-a-bouncing-ball-for-infinite-number-of-bounces-using-sympy
    /*              _
      ___ _ __   __| |
     / _ \ `_ \ / _` |
    |  __/ | | | (_| |
     \___|_| |_|\__,_|

    */
