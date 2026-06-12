---
title: "JMF environment variable Problem"
date: 2007-05-07
forum: Desktop Environments
---

### Post by alanwu on 2007-05-07
I have installed the jmf and set up the environment variable for it. However, when I run an applet that require the jmf, it can not find the jmf, but application can. Could anyone tell me how to sucessfully set up the jmf?

---

### Post by alanwu on 2007-05-07
Nobody knows? I am dying for this

---

### Post by KsR on 2007-05-16
Hi everyone, 

I have been trying to install jmf too for quite sometime.  On searching these forums I have found two solutions, which are working on my system (edgy)

First solution is to check out this site, the easy way out:
[http://isee.anywebcam.com/text/Dracosto.html](http://isee.anywebcam.com/text/Dracosto.html)

The JMF Diagnostics applet at the sun site will recognize the JMF classes if follow the steps given in link above. This link basically explains where to copy the jmf.jar file and other .so files in a few folders where  your java is installed.  Link below
[http://java.sun.com/products/java-media/jmf/2.1.1/jmfdiagnostics.html](http://java.sun.com/products/java-media/jmf/2.1.1/jmfdiagnostics.html)

Another solution is to set you environment variables, which is explained by mustang in this link:
[http://ubuntuforums.org/showthread.php?t=107510&highlight=jmf+classpath](http://ubuntuforums.org/showthread.php?t=107510&highlight=jmf+classpath)
Just add these lines
```
export JMFHOME=/home/someuser/JMF-2.1.1e
export CLASSPATH=$JMFHOME/lib/jmf.jar:.:$CLASSPATH
export LD_LIBRARY_PATH=$JMFHOME/lib:$LD_LIBRARY_PATH
``` at the end of your .bashrc file. NOTE: change the path of JMFHOME to where you have extracted JMF
Save the file and exit any terminal.
Now when you run the Diagnostics applet, the applet will NOT recognize the JMF classes(atleast thats what happened to me)
..BUT.. your program which uses the JMF API will compile and run correctly
sounds kinda weird to me but it works..:)

---

