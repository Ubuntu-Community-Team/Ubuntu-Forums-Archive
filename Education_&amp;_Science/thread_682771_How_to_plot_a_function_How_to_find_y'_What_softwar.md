---
title: "How to plot a function? How to find y'? What software to use?"
date: 2008-01-30
forum: Education &amp; Science
---

### Post by Zdravko on 2008-01-30
Hi there!
I have a course project in Mechanics to do!
One of the tasks requires to write/use a software program that draws the graph of a function and its derivative (separately).
I found already the function y=y(phi), where 0<=phi<=2p. I have already computed the y' analytically, but wonder whether there is a way to compute y' numerically?
And then display their graphs, eventually to make a comparison between the analytical and numerical differentiation.

I'd appreciate any suggestions!


One more thing!
Another task is about a trajectory of a bullet. The initial speed and angle is given. The movement equation must be found. Okay - I found it! :) It has the form:
> x"=f(x', y')
y"=g(x', y')
Then, numerically, must be found/plot:
> x=x(t)
y=y(t)
x=x(y)
y=y(x)
Also, numerically, find (x=?, y=0) and V where the bullet falls on the ground.
If only I could a way to solve this...

---

### Post by TheWizzard on 2008-01-30
You can use C
it is explained in Simulating Ecological and Evolutionary Systems in C
[http://books.google.com/books?hl=en&id=cVrHn-gSAFoC&dq=simulating+ecological&printsec=frontcover&source=web&ots=irbtLx2ziq&sig=Xzd3IYnq22ZhrnAEANhtSJR6AiM#PPP1,M1](http://books.google.com/books?hl=en&id=cVrHn-gSAFoC&dq=simulating+ecological&printsec=frontcover&source=web&ots=irbtLx2ziq&sig=Xzd3IYnq22ZhrnAEANhtSJR6AiM#PPP1,M1)

if you want something easier, you can check out koctave and scilab
or openoffice...

---

### Post by Zdravko on 2008-01-30
I want something easier. What are these koctave?
Btw, I know C and C++.

---

### Post by Zdravko on 2008-01-30
Hmm, koctave seems KDE based :(
Scilab isn't in the repos?

---

### Post by TheWizzard on 2008-01-30
there's no problem using a kde-based app in gnome

---

### Post by Zdravko on 2008-01-30
Okay. If you say so...
But then you will have to help me solve the tasks. It ain't difficult for you, master of mathematics ;)

---

### Post by TheWizzard on 2008-01-30
> **Zdravko said:**
> Hmm, koctave seems KDE based :(
Scilab isn't in the repos?

[http://www.google.nl/search?q=scilab&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a](http://www.google.nl/search?q=scilab&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:official&client=firefox-a)

---

### Post by Zdravko on 2008-01-30
I already downloaded Octave. Now isn't there a way to use it instead of Koctave? 50 MB+ to download is too much for me?
I am just asking. If it is not possible to solve these questions with Octave, just tell me.

---

### Post by TheWizzard on 2008-01-30
> **Zdravko said:**
> Okay. If you say so...
But then you will have to help me solve the tasks. It ain't difficult for you, master of mathematics ;)

koctave is a kde version of gnu octave. use the latter if you're on gnome!

sorry, i'm kde-biased

---

### Post by Zdravko on 2008-01-30
Ok, I am going to use Octave.
Let's start with the plotting of the functions. This must be easy to start?

---

### Post by TheWizzard on 2008-01-30
check
[http://www.gnu.org/software/octave/doc/interpreter/](http://www.gnu.org/software/octave/doc/interpreter/)

---

### Post by Zdravko on 2008-01-30
There is a problem with Octave:
> octave:10> a=[1,2,3]
a =

   1   2   3

octave:11> plot(a)
warning: broken pipe -- some output may be lost
warning: broken pipe -- some output may be lost
warning: broken pipe -- some output may be lost
warning: broken pipe -- some output may be lost
warning: broken pipe -- some output may be lost
warning: broken pipe -- some output may be lost
warning: broken pipe -- some output may be lost
warning: broken pipe -- some output may be lost
warning: broken pipe -- some output may be lost
warning: broken pipe -- some output may be lost
warning: broken pipe -- some output may be lost
warning: broken pipe -- some output may be lost
warning: broken pipe -- some output may be lost
warning: broken pipe -- some output may be lost
warning: broken pipe -- some output may be lost
warning: broken pipe -- some output may be lost
warning: broken pipe -- some output may be lost
warning: broken pipe -- some output may be lost
warning: broken pipe -- some output may be lost
warning: broken pipe -- some output may be lost
warning: broken pipe -- some output may be lost
warning: broken pipe -- some output may be lost
error: `have_newer_gnuplot' undefined near line 333 column 8
error: evaluating binary operator `||' near line 333, column 27
error: if: error evaluating conditional expression
error: evaluating if command near line 333, column 4
error: evaluating switch command near line 245, column 7
error: evaluating for command near line 241, column 5
error: evaluating if command near line 29, column 3
error: called from `__go_draw_axes__' in file `/usr/share/octave/2.9.12/m/plot/__go_draw_axes__.m'
error: evaluating switch command near line 57, column 4
error: evaluating for command near line 55, column 2
error: evaluating if command near line 37, column 7
error: evaluating if command near line 30, column 5
error: evaluating if command near line 29, column 3
error: called from `__go_draw_figure__' in file `/usr/share/octave/2.9.12/m/plot/__go_draw_figure__.m'
error: evaluating if command near line 61, column 6
error: evaluating if command near line 58, column 4
error: evaluating if command near line 56, column 2
error: evaluating for command near line 55, column 7
error: evaluating if command near line 38, column 5
error: called from `drawnow' in file `/usr/share/octave/2.9.12/m/plot/drawnow.m'


Why is that?

---

### Post by ahmatti on 2008-01-30
I think you don't have gnuplot installed. Octave uses it for plotting so to solve your problem install it:
```
sudo apt-get install gnuplot
```

---

### Post by Zdravko on 2008-01-31
I installed it. Now, look at this:
> #! /usr/bin/octave -qf
1;

global L1 = 0.5
global L2 = 0.15
global L4 = 0.1
global L5 = 0.2

function phi4 (phi2)
    global L1
    global L2
    phi4 = acos( (L1 + L2*cos(phi2)) / sqrt(L1^2 + L2^2 + 2*L1*L2*cos(phi2)) )
endfunction

function y6 (phi2)
    global L4
    global L5
    f = @phi4
    y6 = L4*sin(f(phi2)) + L5*sqrt(1 - ((L4/L5)^2)*((cos(f(phi2)))^2))
endfunction

t = 0 : 0.1 : 2*pi;
plot(t, y6(t))
Running it from the terminal issues:
> 
zdravko@ubuntu:~$ ./octave_script1.m
f =

phi4

phi4 =  0.20484
error: sin: argument undefined
error: evaluating binary operator `*' near line 19, column 9
error: evaluating binary operator `+' near line 19, column 23
error: evaluating assignment expression near line 19, column 5
error: called from `y6'
error: evaluating argument list element number 2
error: near line 23 of file `./octave_script1.m'


Why is that?

---

### Post by Zdravko on 2008-01-31
I managed this problem.

---

### Post by Tharmas on 2008-02-12
Maybe you could solve your problem with something much simpler like "just" gnuplot, OO.o Calc, labplot or even qalculate...

---

### Post by Zdravko on 2008-02-12
Sure I could. But I did already the task in Octave. The exam is over. Next semester now :)

---

### Post by subzero27 on 2008-02-14
I think c has a function called coordinates()

---

### Post by Telescope_Nerd on 2008-02-25
x

---

### Post by konrad1811 on 2008-09-12
I recomend my own software:

[www.peplot.com]("http://www.peplot.com")

This can plot:

- analytical functions
- data points with deviations (X and/or Y)
- bar charts (also from raw data)

It can combine these 3 charts types. You may also manage many chart properties and save entered data and evaluated chart.

:lolflag:

---

### Post by Zdravko on 2008-09-15
Interesting.

---

