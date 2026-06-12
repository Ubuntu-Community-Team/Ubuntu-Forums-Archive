---
title: "Compiz dislikes Math software (maple, mathematica)?"
date: 2007-12-04
forum: Desktop Effects &amp; Customization
---

### Post by dcampbell on 2007-12-04
Mathematica opens up two extra blank windows which are it's kernel windows according to what I found on this forum, and Mathematica's site, no solution is currently available.  When I start Maple under compiz it loads the splash screen and an empty window, if I click around in the empty window I can get menus to come up.  I found no suggestions for this on the forum or with google.  Both these problems can be solved by turning off compiz, starting the programs, then turning compiz back on.  I was wondering if anyone had any better suggestions for these problems.

---

### Post by pritamps on 2007-12-04
I had a similar problem with Matlab. Add the following line to your $HOME/.bashrc. 

export AWT_TOOLKIT=MToolkit

And restart terminal or X server (I don't remember what was needed)...that's all it took for me :)

---

### Post by stringkarma on 2008-01-11
I am having the same problems! A work around for Mathematica that isn't too terrible is to right click on the menu bars of the unnecessary windows and move them to another workspace. Still annoying but livable. Maple is very frustrating. Do the programmers of either software know of these issues?

---

### Post by stringkarma on 2008-01-11
Actually with a little surfing I found[ this]("http://forum.ubuntu-fr.org/viewtopic.php?pid=1413966") from the french equivalent to this site. I actually can speak enough french to think he is on to something, but not good enough at linux to actually do what he says. Some one want to try? Google has a page translator if you need it.

---

### Post by alterdaxter on 2008-01-12
> **stringkarma said:**
> Actually with a little surfing I found[ this]("http://forum.ubuntu-fr.org/viewtopic.php?pid=1413966") from the french equivalent to this site. I actually can speak enough french to think he is on to something, but not good enough at linux to actually do what he says. Some one want to try? Google has a page translator if you need it.

down here it worked out great...
just do what is discribed on the french page...

gr

korneel

---

### Post by pstickar on 2008-01-12
> **pritamps said:**
> ...
export AWT_TOOLKIT=MToolkit
...

I have the problems with Mathematica (2 extra blank windows) and Matlab (every window is blank).
I tried your approach and I got:

```
Unable to initialize com.mathworks.mwswing.MJStartup
java.lang.UnsatisfiedLinkError: Can't load library: /usr/share/Matlab/sys/java/jre/glnxa64/jre1.6.0/lib/amd64/motif12/libmawt.so
        at java.lang.ClassLoader.loadLibrary(Unknown Source)
        at java.lang.Runtime.load0(Unknown Source)
        at java.lang.System.load(Unknown Source)
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(Unknown Source)
        at java.lang.ClassLoader.loadLibrary(Unknown Source)
        at java.lang.Runtime.loadLibrary0(Unknown Source)
        at java.lang.System.loadLibrary(Unknown Source)
        at sun.security.action.LoadLibraryAction.run(Unknown Source)
        at java.security.AccessController.doPrivileged(Native Method)
        at sun.awt.NativeLibLoader.loadLibraries(Unknown Source)
        at sun.awt.DebugHelper.<clinit>(Unknown Source)
        at java.awt.Component.<clinit>(Unknown Source)
        at javax.swing.ImageIcon.<clinit>(Unknown Source)
        at com.mathworks.mwswing.desk.Desktop.<clinit>(Desktop.java:103)
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Unknown Source)
        at com.mathworks.jmi.OpaqueJavaInterface.findClass(OpaqueJavaInterface.java:470)
 Failed to start the Desktop: Failure loading desktop class
```

BTW, each time .bashrc is modified, opening a new terminal is enough to get it working (on the new terminal...).

Edited: ------------------------
It's me again. Just found a solution to my problem: edited /usr/local/bin/matlab, so the first two lines now read:

```

#!/bin/sh
export MATLAB_JAVA=/usr/lib/jvm/java-6-sun/jre/

```

Now I continue looking for a solution to the problem of the extra blank screens when using Mathematica.

---

### Post by boirax on 2008-01-19
Hi, I had the same problem with Maple.  

Here is some advice I received from Mohammad Ghebleh (a developer for Maple) with completely solved the problem (both under Edgy Eft and Gutsy Gibbon):

> I realized that this problem occurs only when using AIGLX. I found out in Beryl forums that defining an environment variable solves the problem. I added the following to my .bashrc file and the problem is resolved: 

```
export AWT_TOOLKIT=MToolkit
```

So that is, you can find the file /etc/bash.bashrc and edit it as root (or with sudo) adding

 export AWT_TOOLKIT=MToolkit 

at the end of it.  The next time you start xmaple it should work fine.

Good luck

---

### Post by liuzerus87 on 2008-01-19
Here's a fix to the Mathematica blank windows problem from another thread.  I think all it does it hide the windows without actually solving the problem, but hey, it worked for me.

[http://ubuntuforums.org/showpost.php?p=4140884&postcount=14]("http://ubuntuforums.org/showpost.php?p=4140884&postcount=14")

---

### Post by stringkarma on 2008-01-23
> **alterdaxter said:**
> down here it worked out great...
just do what is discribed on the french page...

gr

korneel

OK that worked. Have you noticed any problems printing now? When I click print it doesn't even show me a dialog box or anything. I am looking to see if this is related to the fix that we worked.
Thanks.

BTW the mathematica fix just above seems to be just the ticket.

---

### Post by paulita on 2008-03-13
Please i need some help..  i can't even start Mathematica 6.0 on my ubuntu feisty. When i start, everything freezes

---

