---
title: "EES (Engineering Equation Solver) clone for Linux"
date: 2007-09-02
forum: Education &amp; Science
---

### Post by HUNTtheHIPPO on 2007-09-02
I know scientific software clones get talked about a lot but I couldn't find any info on this particular one.

F-chart makes a program called EES (Engineering Equation Solver). Its very easy to use and handles units very well. An example of an EES program would be:

F = 7 [kN] * convert(kN,N)
m = 2 [g] * convert(g,kg)
F = m*a

Then when you calculate EES come back with:

F = 7 [N]
m = 2 [kg]
a = 3.5 [m/s^2]

As you can see you don't have to do any algebra or unit conversion because EES does it all for you. Its a real time saver, when doing homework. 

Oh, also note that the equations are not entered in one line at a time like in Octave or Maxima, but the entire code is written and then compiled at one, I find this much easier to edit if I have to change something.

My Thermo & Fluid Mech textbooks came with a trial version of EES that I was running in Wine, but it expired yesterday. 

So my question is are there any Open Source (even just free) programs that have this kind of functionality?

---

### Post by euler_fan on 2007-09-02
I'd be very surprised if Maxima, SciLab, or Octave do not have the ability to run scripts . . . especially since that is a big part of Matlab and Octave and Scilab are designed to compete with it.

---

### Post by HUNTtheHIPPO on 2007-09-02
You're right euler_fan, I should not have said that you could not run scripts in Octave. 
I'll revise what I am looking for:
A simultaneous nonlinear equation solving, that is easy to enter, easy to read, and handles units well.

On your prompting though I'll look over how to make Octave/SciLab scripts to see if they have the functionality I desire.

---

### Post by euler_fan on 2007-09-02
> **HUNTtheHIPPO said:**
> You're right euler_fan, I should not have said that you could not run scripts in Octave. 
I'll revise what I am looking for:
A simultaneous nonlinear equation solving, that is easy to enter, easy to read, and handles units well.

On your prompting though I'll look over how to make Octave/SciLab scripts to see if they have the functionality I desire.

Any of those should have fine simultaneous equation solver capabilities . . . especially for linear systems. The problem you are most likely to run into involve solving non-linear systems and also units. I would not be surprised if none of those systems have the units handling you want out of the box. Usually it is more convenient to standardize your units before hand and not have the solvers worry about them. They aren't going to suddenly change the units you're working with.

---

### Post by jherz on 2008-03-22
For me, not handling units automatically is a real deal breaker. I do DEARLY love my old MathCAD. It does not work under WINE. I could get along fine with Octave as a replacement except for the unit thing. Of course part of it is that in this day and age in the US, it is so convenient to enter your data as you find it in whatever units it comes in and then specify the results in whatever system you need, SI or English. But far more important to me is how easy it makes it to find errors. If you have a bunch of equations and you specify the results in  Coulombs and your result looks like:
                         134.3 Coulomb*length*time^-1
then you know you went wrong somewhere. If I could get similar results from Octave or Maxima I would be a very happy Linux user.

Jonathan Herz

---

### Post by lochlan on 2009-02-01
I also really like EES, though there are a lot of things it doesn't do.  I would love to see how the unit solving works.  Each variable has to be saved as a tuple? with a magnitude and a string that describes it's units.  Then maybe regex the string for each calculation so you know if you've made a unit error?  The built in functions are fantastic, lots of property values, and engineering equations.

---

### Post by naguillo on 2010-12-26
Hello, I have developed an Engineering Equation solver clone. I have created it with java so it works perfectly on Linux, I have tested it on Ubuntu 10.04 -Lucid-, 9.10 -Karmic- and 9.04 -Jaunty-.
It is open source (LGPL), in includes thermodynamic functions, initial value and algorithm selection, Save/Load, Undo/Redo,...

I hope you will give it a try.

[https://code.google.com/p/engineeringsuite/](https://code.google.com/p/engineeringsuite/)

---

### Post by PC_load_letter on 2010-12-28
Just for anyone reading this thread in the future, solving one or a system of nonlinear equations is done in Octave w/ the command fsolve, it's fairly straightforward, see e.g. here: 
[http://www.math.uic.edu/~hanson/Octave/OctaveNonlinearEG.html](http://www.math.uic.edu/~hanson/Octave/OctaveNonlinearEG.html)

---

### Post by BFris on 2011-04-08
I've been using the CompPad extension for OpenOffice/LibreOffice lately. It's pretty amazing. It uses the built in formula editor to do calculations. And it handles units. Charts are done using OO/LibO charts.

Octave/Scilab have a slightly different focus and don't really handle units well. That's not a criticism: I use Octave all the time.

Maxima/wxMaxima can do lots of symbolic manipulations and it can handle some units. I have found it difficult to get MathCAD-like functionality out of Maxima.

---

### Post by phneoix on 2012-01-29
you can try ascend [http://www.ascend4.org/](http://www.ascend4.org/)

---

### Post by BeRoot ReBoot on 2012-02-01
wxMaxima does units out-of-the-box.

```
(%i1)    load(physical_constants)$
(%i2)    a: (10000`ft)/(3`day)$
(%i3)    float(a)``(mile/h);
(%o3)    0.026304713804714`(mile/hour)
```

---

### Post by MySchizoBuddy on 2012-04-15
you can also try [Smath](http://en.smath.info/forum/default.aspx?g=posts&t=1223), A free Linux alternative to Mathcad

---

### Post by MySchizoBuddy on 2012-04-15
thanks for this program.

---

