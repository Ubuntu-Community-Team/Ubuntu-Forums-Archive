---
title: "Software for Engineers"
date: 2008-10-27
forum: Education &amp; Science
---

### Post by nebu on 2008-10-27
I wanted the closest open source alternatives to 

  1. Mathematica
  2. Multisim
  3. AutoCAD
  4. Maya

Is maxima is good option to replace mathematica:confused::confused:

---

### Post by cb951303 on 2008-10-27
> **nebu said:**
> I wanted the closest open source alternatives to 

  1. Mathematica
  2. Multisim
  3. AutoCAD
  4. Maya

Is maxima is good option to replace mathematica:confused::confused:

1. Maxima is quite good. I'm engineer too and when I need CAS, maxima suits all my needs. There were some benchmarks comparing maxima to mathematica. I remember mathematica being better at some tests but the maxima version used was too old.

2. I don't know about that software

3. Although there are some CAD solutions in linux they are not as good as AutoCAD or Solidworks. I think the most mature mechanical cad for linux is VariCAD. It's not sketch based but good enough. At least it has a big component library. I wouldn't recommend it for architecture though.

4. One word: Blender !!

---

### Post by nebu on 2008-10-27
multisim is a software based on spice.... it helps in simulating electronic circuits.....

---

### Post by cb951303 on 2008-10-27
> **nebu said:**
> multisim is a software based on spice.... it helps in simulating electronic circuits.....

you can always use SPICE :) it's open source and works in linux. there is also GNUCAP

they are both CLI of course.

---

### Post by thelinuxer on 2008-10-27
> **cb951303 said:**
> you can always use SPICE :) it's open source and works in linux. there is also GNUCAP

they are both CLI of course.

I search for gnucap and I found this :

gspiceui - A graphical user interface for gnucap and ngspice

Haven't tried it, so I can't say anything about it

---

### Post by Battalion on 2008-11-18
Has anyone tried to Wine install Solidworks? Or use virtual box or any other windows simulator?

---

### Post by cb951303 on 2008-11-18
> **Battalion said:**
> Has anyone tried to Wine install Solidworks? Or use virtual box or any other windows simulator?

I tried nothing worked. With virtualization software you have opengl problem and wine is just not there yet.

However since then, I found out that UniGraphics NX (siemens) works on linux  which is a very good CAD software. It can also do CAM CAE if you have the appropriate addons.

---

### Post by neoflight on 2008-11-18
some listings are give [here]("http://caejournal.com"). Also in my sig.

---

### Post by Battalion on 2008-11-19
> **cb951303 said:**
> I tried nothing worked. With virtualization software you have opengl problem and wine is just not there yet.

However since then, I found out that UniGraphics NX (siemens) works on linux  which is a very good CAD software. It can also do CAM CAE if you have the appropriate addons.

I have never used UniGraphics although people do speak highly of it.  How much will it cost for the base installation without the fancy addons?

---

### Post by kaspar_silas on 2008-11-19
Maxima is really nice but to be brutally honest it's no where near as easy to use or as flexible as mathematica. In fact Mathematica is the one piece of software I haven't been able to replace with open source.

If however you only use small bits of mathematica you may well be able to replace it.

---

### Post by Battalion on 2008-11-19
Mathematica is great honestly, but for everything i do prefer Matlab which has a proper (fully functional) linux version which i'm currently running on Intrepid Ibex right now.  Maxima is good for elementary calculations and getting simple integrals or derivatives of functions, but for real engineering stuff...u really need more than just that!

---

### Post by kaspar_silas on 2008-11-24
I hate to get all pro mathematica as their pricing is simply ridiculus and unfair to non educational users. Plus I trully hate that you have to pay again for plug in modules after speeding a fortune of the main program. 

But that said, there are quite a few areas that mathemtica does come out ahead of pretty much anything else. Sometimes this is due to it doing calculations symbolically or the massive amount of specialised built in mathematical functions. Of course (for the hard core maths folk) there are always Fortran? libraries that will run faster. But an average joe isn't going to use these, nowadays.

O one thing I also only use the linux version of mathematica. Did you think I was wining it? Mathematica actually suits linux given they are now pushing grid computing. 

btw I am not knocking Matlab. There are many places in can be superior to mathematica. Especially for interfacing with other kit in which it is a dream. However I think I could replace my Matlab use with R, Octave or even plain old c when I need power.

---

### Post by mempman on 2008-11-24
for math software on linux, try Maple.

---

### Post by brunovecchi on 2008-11-26
For Perl enthusiasts, there's [**PDL**]("http://pdl.perl.org/") (Perl Data Language).

It's a huge Perl module that allows to do heavy numeric calculations using a new variable type, the "piddle" (it supports multi dimensional matrixes).

It has a very simple syntax, and if you already know the basics of the Perl language, it's all you'll need.

If you prefer Python, there's also the SciPy and NumPy libraries, that provide the same functionality.

---

### Post by hambone79 on 2008-11-26
> **cb951303 said:**
> I tried nothing worked. With virtualization software you have opengl problem and wine is just not there yet.

However since then, I found out that UniGraphics NX (siemens) works on linux  which is a very good CAD software. It can also do CAM CAE if you have the appropriate addons.

I guarantee it is alot more than you want to spend. Last I heard the base license of Unigraphic NX is comparable to a Pro/E license which is around $5000.

You could always do what I do...setup your own Pro/E configuration and login to your company VPN to pull a license. Just be careful though...some companies have employee agreements that will consider any models/drawings created with their license as their own.

---

