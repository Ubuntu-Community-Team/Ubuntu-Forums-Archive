---
title: "3D Polyhedrons"
date: 2011-02-26
forum: Education &amp; Science
---

### Post by schievelbein on 2011-02-26
I am looking all over for a program that will let me draw simple polyhedrons in 3D space, for dice with numbers on each side, preferably using simple commands. I then want to be able to duplicate the shape, for example, have 10 6-sided dice in a row.  The last thing I want to be able to do is program some rules, such as if I move a dice from side '1' facing forward to side '4' facing forward, then the dice to the left rotates on the X axis, and the dice to the right rotates on the Y axis. 

I have different molecules that have different magnetic properties that I want to program the interactions with, and see how they react when I start having dozens of polyhedrons and the 100s of associated actions.

I have searched under '3D State Models' and 'Molecular Animations' and many similar things, but I must be missing it somewhere.  Any and all suggestions are welcomed.

---

### Post by PC_load_letter on 2011-02-27
did you try [_SAGE_]("http://sagemath.org")?

**EDIT:** SAGE 3D plotting does not work properly with the installed-by-default OpenJDK (openJDK has a bug). Sage uses a JAVA applet to render the 3d plots, it's called JMOL and has been originally used to visualize 3D molecules. You'll need to uninstall OpenJDK and install Sun Java packages from Synaptic. 

Also, do NOT install SAGE from the repos (I think they took it off already from 10.10 or they intend to). Just download the .deb binary from the web site.

---

