---
title: "Matlab r2007a GUI"
date: 2009-05-03
forum: Education &amp; Science
---

### Post by allenbradley on 2009-05-03
Matlab r2007a installs fine, but when I run it, the File, Edit etc. tabs are missing. I have attached a screenshot. Whats wrong? Should I request a new copy ( it is, however, something I would like to avoid )

---

### Post by allenbradley on 2009-05-03
Screenshot attached :

---

### Post by allenbradley on 2009-05-05
Finally a solution! After a day of hard searching : 
[http://ubuntuforums.org/archive/index.php/t-529640.html](http://ubuntuforums.org/archive/index.php/t-529640.html)
The last post has the solution.

However, the solution does not work with OpenJDK. I recommend going to the sun website and downloading the JRE and adding the path.

---

### Post by perroazul on 2009-05-06
hi, 
I have the same problem and its solved by disabling compiz (the visual effects). you can re-enable them after you finish your matlab session

---

### Post by Avoozl on 2009-05-18
I have this problem too, but I believe the problem was only related to Matlab using the wrong version of java as was noted above.  I export the correct java version and it runs fine with Compiz still running.

---

### Post by icivilion on 2009-05-22
How to download exact version of java..... i have installed compiz switch installed when i switch it off matlab works fine.... if you know what is the correct version of java i will try it and how to install it please guide!!!!

---

### Post by Avoozl on 2009-05-27
The latest version of Sun's Java works fine for me.  I run this script from a terminal:

```
export MATLAB_JAVA=/usr/lib/jvm/java-6-sun/jre
/opt/matlab/bin/matlab
```

Assuming those are the locations of java and matlab on your machine it should work for you too, even with compiz still running.

---

### Post by XCan on 2009-05-27
At the beginning I thought I would try to limit my use of closed source stuff and too installed OpenJDK and its plugins. Now I've come to realize that OpenJDK unfortunately is crap and does all kinds of random things to my java apps, such as Jabref/imageJ/Matlab and java applets through the Firefox plugin. 

To be honest, I find that the easiest way to remedy all this was just to wipe openjdk from my Ubuntu and install Sun's Java. This will make the default JRE Sun's as well. This way you won't have to mess with exporting paths that will have to be altered after every java update.

However, if you want to export the path, I believe the easiest way is to modify the script that starts up matlab, which by default resides in /usr/local/matlab/bin/matlab . Just add (your java path)
```
export MATLAB_JAVA=/usr/lib/jvm/java-6-sun/jre
```
right after the first line #!/bin/sh. :)

---

### Post by nick_berra on 2009-07-27
I was suffering the same button-less Matlab.  I solved is using the same method as XCan above me, however I inserted the line:

export AWT_TOOLKIT="MToolkit"

Worked an absolute treat, now my Matlab is sexy as hell.

---

