---
title: "Move form matlab to Scientific Python"
date: 2008-12-14
forum: Education &amp; Science
---

### Post by Glenn Jones on 2008-12-14
Hi 

I'm not sure where to post this so here we go. I attended a short course about using python as a replacement for matlab a while back and ever since I've been rather curious about it. My main motivation for changing to python is that matlab takes so long to load up on my desktop and generally is very slow and unresponsive. On top of that it's an excuse to learn another programing language. 

So my question is what are peoples experience with changing from matlab to scientific python? What are peoples opinion on matplotlibs plotting quality compared to matlab? 

Thanks

---

### Post by in_flu_ence on 2008-12-14
While I have no extensive experience in python, I foresee a problem when you try to transist from one language to another. For example, some of the older codes in my lab uses Fortran while others are using Matlab/Octave. Sometimes it becomes quite challenging to integrate codes together.

Another thing I like about Matlab is the toolbox which are built-in (e.g. wavelet analysis). That keeps me from using Matlab for some assignments instead of Octave. Just the convenience.

If you are starting from scratch for some scripting, I think maybe it is worth a try. Not sure how much faster (in performance) does python give you but I think it gives you more options in general programming though.

---

### Post by in_flu_ence on 2008-12-14
While I have no extensive experience in python, I foresee a problem when you try to transist from one language to another. For example, some of the older codes in my lab uses Fortran while others are using Matlab/Octave. Sometimes it becomes quite challenging to integrate codes together.

Another thing I like about Matlab is the toolbox which are built-in (e.g. wavelet analysis). That keeps me from using Matlab for some assignments instead of Octave. Just the convenience.

If you are starting from scratch for some scripting, I think maybe it is worth a try. Not sure how much faster (in performance) does python give you but I think it gives you more options in general programming though.

---

### Post by paulnation on 2008-12-15
I just got done using python in a numerical PDE's class and can say the results turned out quite good.  Overall, the scientific packages for python; scipy, numpy, and matplotlib all work quite well and produce quality output.  The only downside is the performance hit you get from scripting.  You can get around this using fancier programming i.e by calling c-code inline and such but it requires some work to use.

---

### Post by iQuizzle on 2008-12-15
python also has a very nice open source plotting package in the style of matlab plotting. so if you're familiar with matlab style plots (or so i'm told), you will not have a hard time switching to it's python counterpart (called matplotlib).

i've never used matlab all that much, but i use matplot for python all the time and think it's great. it also can be embedded under several gui backends like wx and gtk.

---

### Post by Glenn Jones on 2008-12-16
Hi

I've had a quick bash at using numpy and matplotlib and I must admit I'm impressed by the quality of the figures. The convenient thing is that I can run the script in the terminal in the time it takes matlab to load!!!!

I have a quick question regarding matplotlib and setting thandle on the current axis e.g. In matlab its ax=get(gca,'Size',12) how does this translate in matplotlib? 

Cheers

---

