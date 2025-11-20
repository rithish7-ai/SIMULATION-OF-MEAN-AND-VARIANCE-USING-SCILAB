# SIMULATION-OF-MEAN-AND-VARIANCE-USING-SCILAB
## AIM
To write a program for mean, variance and cross correlation in SCILAB and verify the output.

## EQUIPMENTS NEEDED

•	Computer with i3 Processor
•	SCI LAB


## ALGORITHM
1.	Define	the	Function:	Specify the	function	you	want	to	simulate.	For	example, f(x)=sin⁡(x)f(x) = \sin(x)f(x)=sin(x) or any other function.
2.	Generate Sample Points: Decide on the range and the number of sample points. Generate these sample points within the desired range.
3.	Evaluate the Function: Compute the function values at each of these sample points.
4.	Compute Mean, Variance and Cross Correlation: Use Scilab's functions to calculate the mean and variance of the computed function values.
5.	Display Results: Output the computed mean variance and Cross Correlation
   
## PROCEDURE
•	Refer Algorithms and write code for the experiment.

•	Open SCILAB in System

•	Type your code in New Editor

•	Save the file

•	Execute the code

•	If any Error, correct it in code and execute again

•	Verify the generated results


## PROGRAM
clc; clear; close;
function p = pdf(t)
    p = 3 .* (1 - t).^2;
endfunction
function y = integrand_mean(t)
    y = t .* pdf(t);
endfunction
function y = integrand_x2(t)
    y = t.^2 .* pdf(t);
endfunction
a = 0; b = 1;
EX  = intg(a, b, integrand_mean);
EX2 = intg(a, b, integrand_x2);
vX  = EX2 - EX^2;
EY  = intg(a, b, integrand_mean);
EY2 = intg(a, b, integrand_x2);
vY  = EY2 - EY^2;
mprintf("Mean of X   = %g\n", EX);
mprintf("Var(X)      = %g\n\n", vX);
mprintf("Mean of Y   = %g\n", EY);
mprintf("Var(Y)      = %g\n\n", vY);
function r = crosscorr_seq(x, y)
    nx = length(x);
    ny = length(y);
    lags = -(ny-1):(nx-1);
    r = zeros(1, nx + ny - 1);
    idx = 1;
    for lag = lags
        s = 0;
        for n = 1:nx
            m = n - lag;
            if m >= 1 & m <= ny then
                s = s + x(n) * y(m);
            end
        end
        r(idx) = s;
        idx = idx + 1;
    end
endfunction
x = input("Enter reference sequence (e.g. [1 2 3 4]): ");
y = input("Enter second sequence    (e.g. [2 3 4 5]): ");
x = x(:)'; y = y(:)';
r = crosscorr_seq(x, y);
lags = -(length(y)-1):(length(x)-1);
scf(1);
plot2d3(lags, r);
xtitle("Cross-correlation (stem plot)","Lag","r_{xy}(lag)");

## CALCULATION

<img width="193" height="95" alt="image" src="https://github.com/user-attachments/assets/97eb7915-bf0b-42ab-964d-36541780fc36" />

<img width="213" height="119" alt="image" src="https://github.com/user-attachments/assets/0fdd3e54-2840-40e8-9af2-43f6fb01a7b6" />


## OUTPUT

![WhatsApp Image 2025-11-20 at 07 14 01_9ad3b7ef](https://github.com/user-attachments/assets/5b5109fb-3b92-4ab9-8998-bc734ab3a503)


## RESULT

Thus the mean , variance and cross correlation are executed in Scilab and output is verified.
