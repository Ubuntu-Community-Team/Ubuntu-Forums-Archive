---
title: "matlab&amp;ubuntu 8.10"
date: 2009-01-12
forum: Education &amp; Science
---

### Post by plutuz on 2009-01-12
I've recently installed matlab r2008a on my ubuntu 8.10 laptop.
The good news is that it works...the bad one is that simulink is practically impossible to use as it is too slow...

-what can I do? I've tried all the export MATLAB_JAVA=/usr/lib/jvm/java-6-sun/jre/ but nothing works. Paradoxally I've installed the windows version via wine and it works normally!

- Moreover I have a problem in plots as the plot area colors get all mixed up

Thanks

PS I tested a small script .M and it took 0.76s in matlab/linux and 0.67s in matlab/wine...something's wrong :(

---

### Post by preumbra on 2009-01-26
I have r2008 and 8.10 working (no wine).  Here is some history that may help.  I originally tried with 8.04 and had many problems.  In fact I was ready to give up entirely when 8.10 came out.  This made a difference because sun Java 6 u10 came with Intrepid.  Here are the 4 things I did.

1) Install Sun Java from the package manager.

2) Install Matlab via their instructions.

3) Add the export MATLAB_JAVA = <XXX>  (/usr/lib/jvm/java-6-sun/jre/ in my case) to the matlab file in the bin directory.

4) Make sure visual effects are turned off in System->Preferences->Appearance - otherwise there will be problems.

Note:  I had to re-install both Ubuntu and Matlab (via above), due to the messing around with java I did, in order to get things working.  I know that is an extreme action, but I could find no other way.

Note2:  Simulink does not have the nice toolbar in the Linux version - only in the windows version. I put a plague on the Mathworks house for that.

---

