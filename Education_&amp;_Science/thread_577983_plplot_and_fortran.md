---
title: "plplot and fortran"
date: 2007-10-16
forum: Education &amp; Science
---

### Post by Manolicious on 2007-10-16
if you have no idea what plplot is, [http://plplot.sourceforge.net/]("http://plplot.sourceforge.net/")

So far i got the emacs editor, the fortran compiler, and even most of the plplot and libplplot programs through the synaptic.  I am using several fortran programs together through a makefile made by another programmer, and to compile them I noticed I had to give them a new address for the fortran compiler as compared to the previous programmer's .  However, the previous programmer had simply typed "-lplplotf77" to refer to the plplot package, and even though it is the same command on my computer the compiler appears to have trouble finding plplot.  Thoughts, suggestions?  

the most I've been able to get out of someone was to use a "ldconfig" command on certain roots where some plplot libraries are stored.  Can any body explain in more detail how I do this?

---

### Post by harishg on 2007-10-23
> **Manolicious said:**
> if you have no idea what plplot is, [http://plplot.sourceforge.net/]("http://plplot.sourceforge.net/")

So far i got the emacs editor, the fortran compiler, and even most of the plplot and libplplot programs through the synaptic.  I am using several fortran programs together through a makefile made by another programmer, and to compile them I noticed I had to give them a new address for the fortran compiler as compared to the previous programmer's .  However, the previous programmer had simply typed "-lplplotf77" to refer to the plplot package, and even though it is the same command on my computer the compiler appears to have trouble finding plplot.  Thoughts, suggestions?  

the most I've been able to get out of someone was to use a "ldconfig" command on certain roots where some plplot libraries are stored.  Can any body explain in more detail how I do this?

My feeling is that the default location of plplot on your machine is different from his machine.Try the command 

locate plplot 

and check if it is located in the same place as his and change your make file accordingly.

---

### Post by Manolicious on 2007-10-31
First, thanks for replying!  I keep getting the said feeling these threads just disappear in the backpages if they aren't answered within the first few days.

Anyway to update on those interested, I've been able to get the program to run with fortran, though in a half assed form and only after I talked with another linux user who didn't some stuff I may not be able to replicate here.

First, if you check your synampitc manager and look for plplot, it is indeed there, usually poping up in the form of libplplot files.  For me and my friend though, I think we ended up downloading and configure the package on our own in the root folder as a root user.

A lot of the stuff she was doing was the usual configure, make, make install, and ldconfig, with some tweaking here and there, but as it turned out the MOST important problem was that ubuntu doesn't already come with a c++ compiler, so we had to get one through synaptic (it's called g++ there).

As for your idea harishg, I tried that but I still had trouble getting fortran to recognize it.  However, since I got my c++ compiler it can run.

The only problem is that plplot was made to run in-program by calling something called "xwin" in the fortran code, then a separate display window would pop up.  However, now it just gives me a quick error when it's about to plot, and instead just offers me several formates to save the plot and to look at through an image viewing program.

To find this "xwin", I tried the same trick you suggested harishg.  I tried sniffing around on my advisors computer and throwing a program called "kwin" in my usr/bin directory, but this hasn't changed anything either.

However, I'm content that it works.  Thanks for the help anyway!

---

### Post by jeremytaylor on 2007-11-01
I don't use plplot but as it looks similar to pgplot perhaps I can give some advice. 
 
xwin is usually a driver package that is included in the plplot install. When you do your ./configure there will be an option to include xwindows support.

However before you go off and recompile I think the libraries in the repos seem to work fine for me. You should use the pkg-config utility to find the right libraries to link to... do
```
pkg-config --cflags --libs plplotd-f95
```
or
```
 pkg-config --cflags --libs plplotd-f77

```
for fortran 95 or 77

Jeremy

---

