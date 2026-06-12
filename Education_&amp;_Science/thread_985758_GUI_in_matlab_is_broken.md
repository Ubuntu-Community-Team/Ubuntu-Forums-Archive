---
title: "GUI in matlab is broken"
date: 2008-11-17
forum: Education &amp; Science
---

### Post by meandstuff on 2008-11-17
I just got the matlab R2007a student version and installed it on my kubuntu 8.04.  Everything went fine, the installation and registration worked, and in fact I can run matlab- from a konsole.  The GUI is a no-show- a blank screen pops up.  The background command line shows that matlab is trying to use the wrong version of java, but I'm not sure how to tell it to find /usr/lib/jvm/java-6-sun-1.6.0.07 which is what it ought to be using.  If anyone can help, I'd really appreciate it.

N.

---

### Post by meandstuff on 2008-11-18
Problem solved.  I used pico to add a path to the new and improved java to the matlab startup sequence.
code:
sudo pico matlabroot/bin/matlab

this pulls up the matlab code, the first big chunk of which is commented out.  scroll down until you get to the first line of actual code, and add in:
export MATLAB_JAVA=/usr/lib/jvm/java-6-sun-1.6.0.07/jre

substitute whatever your particular java path is, but I imagine that one is pretty standard as I haven't changed much.

Another thing I did earlier which I'm not sure had anything to do with matlab now working:  I edited, also using pico, /etc/jvm to add 
/usr/lib/jvm/java-6-sun-1.6.0.07 
to the TOP of the list of java stuff.

:guitar:

---

