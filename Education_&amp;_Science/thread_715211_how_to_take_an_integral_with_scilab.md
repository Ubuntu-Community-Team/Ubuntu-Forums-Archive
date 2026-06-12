---
title: "how to take an integral with scilab?"
date: 2008-03-04
forum: Education &amp; Science
---

### Post by meborc on 2008-03-04
Hi,

i have been searching the open web for the answer and i get nothing :) i know the question is very easy, but i am a beginner with scilab so easy is hard for me :(

can anyone explain me how to take an integral from a to b from function x ? what is the most simple way to do this?

i hate doing with a scientific calculator, i would like to use scilab for all my calculations

i have tried the "scilab for dummies" paper, but it has nothing on integrals

thanks

a numerical example would be great :D

---

### Post by Whiffle on 2008-03-04
I can do it with Octave in a numerical fashion pretty easily, havn't done much in scilab though.

---

### Post by meborc on 2008-03-04
how do you do it in octave? can you give me an example?

---

### Post by Whiffle on 2008-03-04
[http://www.math.uic.edu/~hanson/Octave/OctaveIntegralEG.html](http://www.math.uic.edu/~hanson/Octave/OctaveIntegralEG.html)

---

### Post by meborc on 2008-03-04
thank you very much :)

if someone has some insights on scilab, i would be interested in that too

---

### Post by NilsHG on 2008-03-04
I am using Maxima when my basic calculator is insufficient for the job.

"Maxima is a computer program for doing mathematics calculations, symbolic manipulations, numerical computations and graphics."

```
sudo apt-get install xmaxima
```

it does provide examples on the front page on how to do various calculations. solving integral problems is very easy. you should be able to do this after looking at the examples.

---

### Post by WW on 2008-03-04
The function is called **integrate**; try **help integrate** in Scilab.

For example:
> 
-->function y = sq(x), y = x^2, endfunction
 
-->j = integrate('sq(x)','x',0,1)          
 j  =
 
    0.3333333  
 
-->


---

### Post by meborc on 2008-03-04
> **WW said:**
> The function is called **integrate**; try **help integrate** in Scilab.

For example:

thank you :)

(the help seems to be broken in the gutsy repo scilab version)

---

### Post by PeterP24 on 2008-03-08
Tthe function required for doing a definite integral in Scilab is intg. If you need the integral of the function f, over an interval [a,b] you first have to define that function like below :

// the function named "something" receive the x argument and return the y output:
function y=something(x),y=x^2+1,endfunction
//and here is the integral of that polynomial x^2+1 over the [0 ... 1] interval:
I=intg(0,1,something)


If you need more help type : help intg at Scilab prompt. It will show you ways to integrate function defined by fortran or C code. 
I have the Scilab and help files  installed from Gutsy repositories via Synaptic Package Manager, and both are working fine.

Best regards 

Peter

---

### Post by WW on 2008-03-08
Ah, **intg**, I didn't see that.   A function like intg makes more sense than integrate; having to pass strings to integrate seemed strange.  intg is certainly faster:

```

-->function y=myfunc(x), y = sin(x^2)^2, endfunction

-->tic(); w = intg(0,50,myfunc), elapsed_time = toc()              
 w  =
 
    24.780913  
 elapsed_time  =
 
    0.3  
 
-->tic(); w = integrate('myfunc(x)','x',0,50), elapsed_time = toc()
 w  =
 
    24.780913  
 elapsed_time  =
 
    2.229  
 
-->

```

---

### Post by dariem on 2008-12-18
OK!
but symbolic integration?!

---

### Post by euler_fan on 2008-12-19
[http://www.cert.fr/dcsd/idco/perso/Magni/s_sym/functions.html]("http://www.cert.fr/dcsd/idco/perso/Magni/s_sym/functions.html")

Just a thought.

---

### Post by Proton Soup on 2008-12-19
> **meborc said:**
> thank you :)

(the help seems to be broken in the gutsy repo scilab version)

in case anyone else is wondering about this, it's broken in hardy, too.  you have to either go into synaptic package manager and install scilab-doc, or use something like this:

[http://ubuntuforums.org/showpost.php?p=5767172&postcount=2](http://ubuntuforums.org/showpost.php?p=5767172&postcount=2)

---

