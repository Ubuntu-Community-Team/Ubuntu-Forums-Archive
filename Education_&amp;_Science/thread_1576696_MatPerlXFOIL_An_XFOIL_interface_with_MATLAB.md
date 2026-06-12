---
title: "MatPerlXFOIL: An XFOIL interface with MATLAB"
date: 2010-09-17
forum: Education &amp; Science
---

### Post by azredwing on 2010-09-17
Hi all,

For the past few months, I've been working with XFOIL, an aerospace engineering program used to analyze airfoils. XFOIL is pretty clunky, and from what I've read in the past few months, not many people have successfully used XFOIL in batch effectively to change airfoil parameters, Reynolds/Mach numbers, etc, on the fly.

In the course of my senior design project through the past year, and with the assistance of the Ubuntu and Linux community, I've developed MatPerlXFOIL (MPXF), a MATLAB function that utilizes a Perl backend to interface with XFOIL. This allows someone using MATLAB and XFOIL to directly retrieve lift/drag/moment parameters as a function of airfoil, angle of attack, and flow regime parameters.

This MATLAB function is usable for Linux, Windows, and Mac, although Windows users will need to do some work in installing Cygwin to use it. 

Get it at [https://sourceforge.net/projects/mpxfoil/](https://sourceforge.net/projects/mpxfoil/)

Read the original discussion that inspired this project here: [http://ubuntuforums.org/showthread.php?t=1306747](http://ubuntuforums.org/showthread.php?t=1306747)

I'm not posting this thread necessarily because I want to advertise, but because I have been frustrated at the lack of support for XFOIL, an aerospace engineer's staple engineering program, throughout both the *NIX and Windows world. I'm hoping this thread serves to assist any aerospace engineer in doing their airfoil analysis. Surely, it'll help those in the above-linked thread asking for help with the original script I wrote to do my analysis.

Mods, please PM me and lock the thread down if you feel this is in violation of any rules.

---

