---
title: "matlab install with ISO - install worked can't find matlab"
date: 2008-02-18
forum: Education &amp; Science
---

### Post by christinak on 2008-02-18
Hey hey!

So, I pretty much looked through all of the above threads but somehow none solve my problem.

I tried to install matlab using the direction on the second page of this [http://ubuntuforums.org/showthread.php?t=676523&highlight=installing+matlab](http://ubuntuforums.org/showthread.php?t=676523&highlight=installing+matlab) thread.

(Because i had the usual permission denied problems)

so, it worked, it actually did the install and everything (i could see it...the percent of install etc.) I just followed along and let the install manager put it into /usr/local/bin.

Then, however, it was gone! I installed it again - and nothing. If i search the system which i hope i did correctly this comes:

christina@tinkerbell:~$ locate matlab
/usr/local/maple9.5/examples/matlab.mws
/usr/share/enscript/hl/matlab.st
/usr/share/apps/katepart/syntax/matlab.xml
/usr/share/mime/text/x-matlab.xml

if i change to /usr/local/bin i only find maple....
if I type matlab from anywhere - well, command not found.
where is my matlab? :confused:

I'm sorry if this questioin is really stupid i know i'm not an expert at all but maybe somebody knows help.

thanx a lot in advance!
Cheers,
Christina

---

### Post by mali2297 on 2008-02-18
Have you tried typing **matlab** in the terminal?

The search tool **locate** uses a database that might not have been updated since the installation. To force an update, type **sudo updatedb**.

/Martin

---

### Post by christinak on 2008-02-18
Heyhey!

So, I updated the database, and in fact there was quite a lot - it took a while.

However, if i type matlab in terminal, my pc tells me the command is not found. if i cnange to the directory where apparently all the stuff is and type it there, it doesn't find the command either.

however, typing ls gives me 

christina@tinkerbell:/usr/local/matlab74_sv$ ls
bin     install_matlab      license.txt  stateflow       update
etc     install_matlab.out  patents.txt  sys             work
extern  java                rtw          toolbox         X11
help    jhelp               simulink     trademarks.txt

changing to bin here - he won't do matlab.... ???:confused:

could it be some installation finalizing thing is missing?

Thanks for your help so far though!
Cheers,
Christina

---

### Post by amd-64 on 2008-02-19
matlab command ~matlabroot/bin/matlab does not work because matlab folder is not installed in /usr/bin or somewhere on the path. 

You could link it to /usr/bin as follows

sudo ln -s /usr/local/matlab74_sv/bin/matlab  /usr/bin/matlab

and then executing matlab from the command line should start the GUI

---

### Post by christinak on 2008-02-19
This time it worked!

Thank you so much!!!!

Cheers,
Christina

---

### Post by aJayRoo on 2008-02-19
When you install Matlab, after it asks you which path to install under, it also asks for the link directory. If you ever install again you should set the link path appropriately to avoid the issue.

---

### Post by militem on 2008-02-19
Thanks ajayRoo!  Of course being the genius that I am I wait until the night before a problem set is due to try to install Matlab on an OS I have less than 2 weeks with!  You saved my bacon.

---

### Post by jmlehrfeld on 2009-03-31
So I know this is an old thread by now, but in case anyone is still paying attention here, I have a related problem.  Updating my database fixed the problem of not being able to find Matlab (thanks!), and after that it started up with no problem just by typing Matlab into the terminal.  However, it looks like I may be getting some errors along the way.  Do I need to worry about these?  Here's what's coming up:

```

Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb52ee7c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb52ee96e]
#2 /usr/lib/libX11.so.6 [0xb57e0619]
#3 /usr/lib/libX11.so.6(XGetVisualInfo+0x26) [0xb57d6666]
#4 /home/jmlehrfeld/sys/java/jre/glnx86/jre/lib/i386/xawt/libmawt.so [0xa3084319]
#5 /home/jmlehrfeld/sys/java/jre/glnx86/jre/lib/i386/xawt/libmawt.so [0xa3084565]
#6 /home/jmlehrfeld/sys/java/jre/glnx86/jre/lib/i386/xawt/libmawt.so [0xa30853c9]
#7 /home/jmlehrfeld/sys/java/jre/glnx86/jre/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x2f) [0xa308561f]
#8 [0xafd38ecd]
#9 [0xafd31edd]
#10 [0xafd31edd]
#11 [0xafd2f249]
#12 /home/jmlehrfeld/sys/java/jre/glnx86/jre/lib/i386/client/libjvm.so [0x621c40d]
#13 /home/jmlehrfeld/sys/java/jre/glnx86/jre/lib/i386/client/libjvm.so [0x6310378]
#14 /home/jmlehrfeld/sys/java/jre/glnx86/jre/lib/i386/client/libjvm.so [0x621c2a0]
#15 /home/jmlehrfeld/sys/java/jre/glnx86/jre/lib/i386/client/libjvm.so(JVM_DoPrivileged+0x363) [0x6272153]
#16 /home/jmlehrfeld/sys/java/jre/glnx86/jre/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb1de896d]
#17 [0xafd38ecd]
#18 [0xafd31d77]
#19 [0xafd2f249]

```

---

### Post by mali2297 on 2009-04-03
> **jmlehrfeld said:**
> So I know this is an old thread by now, but in case anyone is still paying attention here, I have a related problem.  Updating my database fixed the problem of not being able to find Matlab (thanks!), and after that it started up with no problem just by typing Matlab into the terminal.  However, it looks like I may be getting some errors along the way.  Do I need to worry about these?  Here's what's coming up:


You seem to have installed Java in your home folder? Perhaps the "PrivilegedAction" error is because Java has not been installed system-wide.

---

### Post by jmlehrfeld on 2009-04-04
> **mali2297 said:**
> You seem to have installed Java in your home folder? Perhaps the "PrivilegedAction" error is because Java has not been installed system-wide.

Thanks Mali!  I'm very much a noob still, could you tell me how to install it system-wide instead of in my home folder?  I don't remember choosing the directory when I did this... or it's also possible that I copied a command line from another forum that happened to have included something to put it in the home folder, I really can't remember...

---

### Post by mali2297 on 2009-04-04
> **jmlehrfeld said:**
> Thanks Mali!  I'm very much a noob still, could you tell me how to install it system-wide instead of in my home folder?  I don't remember choosing the directory when I did this... or it's also possible that I copied a command line from another forum that happened to have included something to put it in the home folder, I really can't remember...

Sun Java is available in the repositories. You can use the package manager Synaptic to install it; search for **sun-java6-jre**. If you cannot find it, check that you have the *multiverse* repository enabled (in the menu Settings -> Repositories).

---

### Post by jmlehrfeld on 2009-04-07
> **mali2297 said:**
> Sun Java is available in the repositories. You can use the package manager Synaptic to install it; search for **sun-java6-jre**. If you cannot find it, check that you have the *multiverse* repository enabled (in the menu Settings -> Repositories).

Ok, thanks again!

---

### Post by subjugater on 2009-05-10
> **jmlehrfeld said:**
> Ok, thanks again!

Hey, man,

I came across exactly the same problem as you. But I think I installed jre system-wide. Did you really solve the issue by following what mali suggested? Thanks to both of you.

---

