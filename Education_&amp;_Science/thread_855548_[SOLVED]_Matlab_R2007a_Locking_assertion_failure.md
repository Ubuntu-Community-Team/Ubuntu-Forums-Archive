---
title: "[SOLVED] Matlab R2007a Locking assertion failure"
date: 2008-07-10
forum: Education &amp; Science
---

### Post by QED314159 on 2008-07-10
When trying to run Matlab R2007a student edition I receive the following message in the terminal.

```

Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb5ae9767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb5ae98b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb5e551bd]
#3 /usr/local/matlab74_sv/sys/java/jre/glnx86/jre1.5.0/lib/i386/xawt/libmawt.so [0xa1fa326a]
#4 /usr/local/matlab74_sv/sys/java/jre/glnx86/jre1.5.0/lib/i386/xawt/libmawt.so [0xa1f89352]
#5 /usr/local/matlab74_sv/sys/java/jre/glnx86/jre1.5.0/lib/i386/xawt/libmawt.so [0xa1f89599]
#6 /usr/local/matlab74_sv/sys/java/jre/glnx86/jre1.5.0/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x24) [0xa1f897a4]
#7 [0xae2a2b7a]
#8 [0xae29ca7b]
#9 [0xae29ca7b]
#10 [0xae29a157]
#11 /usr/local/matlab74_sv/sys/java/jre/glnx86/jre1.5.0/lib/i386/client/libjvm.so [0xb2f798ec]
#12 /usr/local/matlab74_sv/sys/java/jre/glnx86/jre1.5.0/lib/i386/client/libjvm.so [0xb3068378]
#13 /usr/local/matlab74_sv/sys/java/jre/glnx86/jre1.5.0/lib/i386/client/libjvm.so [0xb2f7971f]
#14 /usr/local/matlab74_sv/sys/java/jre/glnx86/jre1.5.0/lib/i386/client/libjvm.so(JVM_DoPrivileged+0x2db) [0xb2fd1ebb]
#15 /usr/local/matlab74_sv/sys/java/jre/glnx86/jre1.5.0/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb356c2cd]
#16 [0xae2a242b]
#17 [0xae29c9a4]
#18 [0xae29a157]
#19 /usr/local/matlab74_sv/sys/java/jre/glnx86/jre1.5.0/lib/i386/client/libjvm.so [0xb2f798ec]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb5ae9767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb5ae981e]
#2 /usr/lib/libX11.so.6 [0xb5e54518]
#3 /usr/lib/libX11.so.6(XGetVisualInfo+0x26) [0xb5e4b0a6]
#4 /usr/local/matlab74_sv/sys/java/jre/glnx86/jre1.5.0/lib/i386/xawt/libmawt.so [0xa1f88227]
#5 /usr/local/matlab74_sv/sys/java/jre/glnx86/jre1.5.0/lib/i386/xawt/libmawt.so [0xa1f884b8]
#6 /usr/local/matlab74_sv/sys/java/jre/glnx86/jre1.5.0/lib/i386/xawt/libmawt.so [0xa1f896e0]
#7 /usr/local/matlab74_sv/sys/java/jre/glnx86/jre1.5.0/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x24) [0xa1f897a4]
#8 [0xae2a2b7a]
#9 [0xae29ca7b]
#10 [0xae29ca7b]
#11 [0xae29a157]
#12 /usr/local/matlab74_sv/sys/java/jre/glnx86/jre1.5.0/lib/i386/client/libjvm.so [0xb2f798ec]
#13 /usr/local/matlab74_sv/sys/java/jre/glnx86/jre1.5.0/lib/i386/client/libjvm.so [0xb3068378]
#14 /usr/local/matlab74_sv/sys/java/jre/glnx86/jre1.5.0/lib/i386/client/libjvm.so [0xb2f7971f]
#15 /usr/local/matlab74_sv/sys/java/jre/glnx86/jre1.5.0/lib/i386/client/libjvm.so(JVM_DoPrivileged+0x2db) [0xb2fd1ebb]
#16 /usr/local/matlab74_sv/sys/java/jre/glnx86/jre1.5.0/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb356c2cd]
#17 [0xae2a242b]
#18 [0xae29c9a4]
#19 [0xae29a157]

```

I tried using the following fix suggested on the Matlab help page 
```

export MATLAB_JAVA=/usr/lib/jvm/java-6-sun-1.6.0.06/jre

```
however I still receive the same result as above.

Any help would be most appreciated.

Thanks.

---

### Post by eldragon on 2008-07-10
have you checked if you got the sun jre 6 installed?

---

### Post by QED314159 on 2008-07-10
sun jre 6 is installed

---

### Post by kleeman on 2008-07-11
Your problem was apparently solved in this thread:



[https://answers.edge.launchpad.net/ubuntu/+question/26562](https://answers.edge.launchpad.net/ubuntu/+question/26562)

---

### Post by QED314159 on 2008-08-03
Sorry of the delay. Thanks for the link to that thread the following solved my problem:

Adding the following as the first line of $MATLABROOT/bin/matlab

"export MATLAB_JAVA=/usr/lib/jvm/java-6-sun-1.6.0.06/jre/"

---

### Post by marcusesses on 2008-08-09
What about Octave?

I know I'm a bit behind the ball on this thread, but it works just as well as Matlab (I've used both), as long as you download a couple additional packages (I use Grace for my plotting...and well, that's it).
Plus, it's cheaper, which makes it very appealing for me...haha

---

### Post by lemboy4 on 2008-08-20
thanks QED314159, that fixed it for me, also

---

### Post by spooner on 2008-09-11
I added this instead as it is a symbolic link that gets updated when you update sun java 6...

export MATLAB_JAVA=/usr/lib/jvm/java-6-sun/jre

---

### Post by eotakos on 2008-09-11
the solution proposed by  kleeman  and  analyticaly described here by QED  fixed the problem for me too.

thanks to both of you

i think the author of the thread should mark this as solved thread, since locking assertion is a problem almost everyone has with matlab. other ubuntu users will appreciate spotting the solution to their problem easier

---

### Post by jormabe1 on 2008-09-13
great!retail and [wholesale wedding dresses](http://www.jormabridal.com/wholesale.html), [mother of bride dresses](http://www.jormabridal.com/special_dress.html), [bridesmaid dresses](http://www.jormabridal.com/gown.html), [flower girl dresses](http://www.jormabridal.com/flower_girl.html), [prom dresses](http://www.jormabridal.com/Prom_dress.html)

---

