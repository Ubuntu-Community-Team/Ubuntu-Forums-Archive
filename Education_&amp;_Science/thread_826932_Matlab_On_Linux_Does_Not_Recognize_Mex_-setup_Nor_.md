---
title: "Matlab On Linux Does Not Recognize Mex -setup Nor Gui"
date: 2008-06-12
forum: Education &amp; Science
---

### Post by anaGP on 2008-06-12
I installed the R2008a without problems, but when I want to use the GUI (guide) appears a screen to activate the license, I indicate the way to him where it is the license file, but when returning to open that or another group GUI it does the same  what can be happening? (simulink works) 
In addition I continue having he himself error (another one) that with other older versions of matlab under linux (in matlab under Windows it does not happen): work with a called bookstore truetime; I must add lines in matlabrc.m so that it recognizes it, of those lines of code works all safe good by the line: mex - setup; matlab under linux does not recognize that code, by error of license 2. 
////// 
Which I add at the end of matlabrc.m: 


disp(’Bienvenidos. A trabajar con TrueTime.’ 
disp(’Espere por favor …’ 
addpath([getenv('TTKERNEL')]) 
init_truetime; 
disp(’Todo bien hasta aca …’); 

mex -setup 

make_truetime; 
HELP ME!!! THANK YOU !!!!

---

