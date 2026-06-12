---
title: "Java and MATLAB on Beryl start with a blank/grey screen"
date: 2007-02-10
forum: Desktop Environments
---

### Post by mattaw on 2007-02-10
**Problem:**

If you are using matlab with beryl, or some other Java application the window starts up blank or grey.

**Solution:**

This is a bug with AWT which is discussed here:

[http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6509038](http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6509038).

To fix it you have to modifiy the Java code:

[LIST=1]
[*]You must enable multiverse in the repositories and install sun's java 6.
[*]Run [FONT="Courier New"]sudo update-java-alternatives -s java-6-sun[/FONT]
[*]Follow the instructions here: [http://wiki.beryl-project.org/wiki/Java](http://wiki.beryl-project.org/wiki/Java) EXCEPT the jre is located in [FONT="Courier New"]/usr/lib/jvm/java-6-sun/jre/[/FONT] NOT [FONT="Courier New"]/usr/java/jdk1.6.0/jre/[/FONT]
[*]Don't get worried by the huge number of warnings the [FONT="Courier New"]javac[/FONT] step creates.
[/LIST]

After this, java should be fully functional on beryl.
To run MatLab we need to tell it to use our modified java 6 instead of its internal java:

[FONT="Courier New"]export MATLAB_JAVA=/usr/lib/jvm/java-6-sun/jre/ && matlab
[/FONT]

---

### Post by one_stinky_bum on 2007-02-13
The javac step doesn't work for me. Here are the errors:
```
----------
1. WARNING in sun/awt/X11/XDecoratedPeer.java (at line 19)
        import java.util.*;
               ^^^^^^^^^
The import java.util is never used
----------
2. ERROR in sun/awt/X11/XDecoratedPeer.java (at line 95)
        void setIconHints(java.util.List<XIconInfo> icons) {
                          ^^^^^^^^^^^^^^
The type List is not generic; it cannot be parameterized with arguments <XIconInfo>
----------
3. ERROR in sun/awt/X11/XDecoratedPeer.java (at line 95)
        void setIconHints(java.util.List<XIconInfo> icons) {
                                         ^^^^^^^^^
Syntax error, parameterized types are only available if source level is 5.0
----------
4. WARNING in sun/awt/X11/XDecoratedPeer.java (at line 275)
        if (getDecorations() == winAttr.AWT_DECOR_NONE) {
                                        ^^^^^^^^^^^^^^
The static field XWindowAttributesData.AWT_DECOR_NONE should be accessed in a static way
----------
5. ERROR in sun/awt/X11/XDecoratedPeer.java (at line 278)
        reshape(dimensions, SET_SIZE, false);
                            ^^^^^^^^
SET_SIZE cannot be resolved
----------
6. ERROR in sun/awt/X11/XDecoratedPeer.java (at line 370)
        reshape(dimensions, SET_BOUNDS, false);
                            ^^^^^^^^^^
SET_BOUNDS cannot be resolved
----------
7. ERROR in sun/awt/X11/XDecoratedPeer.java (at line 372)
        reshape(dimensions, SET_SIZE, false);
                            ^^^^^^^^
SET_SIZE cannot be resolved
----------
8. ERROR in sun/awt/X11/XDecoratedPeer.java (at line 503)
        if ((op & NO_EMBEDDED_CHECK) == 0 && isEmbedded()) {
                  ^^^^^^^^^^^^^^^^^
NO_EMBEDDED_CHECK cannot be resolved
----------
9. ERROR in sun/awt/X11/XDecoratedPeer.java (at line 512)
        op = op & ~NO_EMBEDDED_CHECK;
                   ^^^^^^^^^^^^^^^^^
NO_EMBEDDED_CHECK cannot be resolved
----------
10. ERROR in sun/awt/X11/XDecoratedPeer.java (at line 514)
        if (op == SET_LOCATION) {
                  ^^^^^^^^^^^^
SET_LOCATION cannot be resolved
----------
11. ERROR in sun/awt/X11/XDecoratedPeer.java (at line 517)
        if (op == SET_BOUNDS) {
                  ^^^^^^^^^^
SET_BOUNDS cannot be resolved
----------
12. ERROR in sun/awt/X11/XDecoratedPeer.java (at line 524)
        if (op == SET_BOUNDS) {
                  ^^^^^^^^^^
SET_BOUNDS cannot be resolved
----------
13. ERROR in sun/awt/X11/XDecoratedPeer.java (at line 544)
        switch (operation & (~NO_EMBEDDED_CHECK)) {
                              ^^^^^^^^^^^^^^^^^
NO_EMBEDDED_CHECK cannot be resolved
----------
14. ERROR in sun/awt/X11/XDecoratedPeer.java (at line 545)
        case SET_LOCATION:
             ^^^^^^^^^^^^
SET_LOCATION cannot be resolved
----------
15. ERROR in sun/awt/X11/XDecoratedPeer.java (at line 550)
        case SET_SIZE:
             ^^^^^^^^
SET_SIZE cannot be resolved
----------
16. ERROR in sun/awt/X11/XDecoratedPeer.java (at line 555)
        case SET_CLIENT_SIZE: {
             ^^^^^^^^^^^^^^^
SET_CLIENT_SIZE cannot be resolved
----------
17. ERROR in sun/awt/X11/XDecoratedPeer.java (at line 563)
        case SET_BOUNDS:
             ^^^^^^^^^^
SET_BOUNDS cannot be resolved
----------
18. ERROR in sun/awt/X11/XDecoratedPeer.java (at line 633)
        new Object[] {isReparented(), isVisible(), runningWM, getDecorations()});
                      ^^^^^^^^^^^^^^
Type mismatch: cannot convert from boolean to Object
----------
19. WARNING in sun/awt/X11/XDecoratedPeer.java (at line 637)
        && getDecorations() != winAttr.AWT_DECOR_NONE)
                                       ^^^^^^^^^^^^^^
The static field XWindowAttributesData.AWT_DECOR_NONE should be accessed in a static way
----------
20. WARNING in sun/awt/X11/XDecoratedPeer.java (at line 643)
        if (!insets_corrected && getDecorations() != winAttr.AWT_DECOR_NONE) {
                                                             ^^^^^^^^^^^^^^
The static field XWindowAttributesData.AWT_DECOR_NONE should be accessed in a static way
----------
21. WARNING in sun/awt/X11/XDecoratedPeer.java (at line 1095)
        ((XWindowPeer)target.getPeer()).requestXFocus();
                      ^^^^^^^^^^^^^^^^
The method getPeer() from the type Component is deprecated
----------
22. WARNING in sun/awt/X11/XDecoratedPeer.java (at line 1156)
        setActualFocusedWindow((XWindowPeer)actualFocusedWindow.getPeer());
                                            ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
The method getPeer() from the type Component is deprecated
----------
----------
23. ERROR in sun/awt/X11/XWM.java (at line 1052)
        HashMap<Class<?>, Collection<XProtocol>> protocolsMap = new HashMap<Class<?>, Collection<XProtocol>>();
                ^^^^^^^^^^^^^^^^^^^^
Syntax error, parameterized types are only available if source level is 5.0
----------
24. ERROR in sun/awt/X11/XWM.java (at line 1052)
        HashMap<Class<?>, Collection<XProtocol>> protocolsMap = new HashMap<Class<?>, Collection<XProtocol>>();
                      ^
Syntax error, parameterized types are only available if source level is 5.0
----------
25. ERROR in sun/awt/X11/XWM.java (at line 1052)
        HashMap<Class<?>, Collection<XProtocol>> protocolsMap = new HashMap<Class<?>, Collection<XProtocol>>();
                                                                            ^^^^^^^^^^^^^^^^^^^^
Syntax error, parameterized types are only available if source level is 5.0
----------
26. ERROR in sun/awt/X11/XWM.java (at line 1052)
        HashMap<Class<?>, Collection<XProtocol>> protocolsMap = new HashMap<Class<?>, Collection<XProtocol>>();
                                                                                  ^
Syntax error, parameterized types are only available if source level is 5.0
----------
27. ERROR in sun/awt/X11/XWM.java (at line 1056)
        Collection<XProtocol> getProtocols(Class protocolInterface) {
        ^^^^^^^^^^
The type Collection is not generic; it cannot be parameterized with arguments <XProtocol>
----------
28. ERROR in sun/awt/X11/XWM.java (at line 1056)
        Collection<XProtocol> getProtocols(Class protocolInterface) {
                   ^^^^^^^^^
Syntax error, parameterized types are only available if source level is 5.0
----------
29. ERROR in sun/awt/X11/XWM.java (at line 1636)
        public boolean setNetWMIcon(XWindowPeer window, java.util.List<XIconInfo> icons) {
                                                        ^^^^^^^^^^^^^^
The type List is not generic; it cannot be parameterized with arguments <XIconInfo>
----------
30. ERROR in sun/awt/X11/XWM.java (at line 1636)
        public boolean setNetWMIcon(XWindowPeer window, java.util.List<XIconInfo> icons) {
                                                                       ^^^^^^^^^
Syntax error, parameterized types are only available if source level is 5.0
----------

```

Any help? I'm on AMD64 with edgy and the latest beryl non-svn.

---

### Post by zootm on 2007-02-19
one_sticky_bum: 
It looks a lot like you're not using Java 5/6's source level (which is weird, since I think it should be default). Try adding the switch "-source 1.5" (or "-source 5.0").

---

### Post by one_stinky_bum on 2007-02-19
Doesn't really like it... here is the output:

```
me@me:/tmp/java/rt$ javac -d -source 1.5 . sun/awt/X11/*.java 
directory does not exist: 1.5
me@me:/tmp/java/rt$ javac -d -source 5.0 . sun/awt/X11/*.java 
directory does not exist: 5.0

```

---

### Post by sirdiego on 2007-03-13
hey guys, how can i activate/install the level 5 source.

im a newb in java but have to use it in school and there we have source level 5 and some actions dont run on my ubuntu pc.

greets tim

---

### Post by Buzzdee on 2007-10-27
has anyone copied the instructions from the wiki or recalls how he did it? the wiki is down for a while: "Since this wiki was getting defaced, it will remain closed for a few days until someone gives it some love (secures it, cleans it...) Thanks for your comprehension"

---

### Post by Buzzdee on 2007-10-28
Well, maybe someone can help me then:
I'm running Gutsy 64bit on a lenovo T61p with the restricted NVidia drivers and compiz enabled. I get the very popular blank-screen-in-java-apps problem and found some tips on where to add the following:
```
export MATLAB_JAVA=/usr/lib/jvm/java-6-sun/jre && matlab
Unable to initialize com.mathworks.mwswing.MJStartup
java.lang.UnsatisfiedLinkError: Can't load library: /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/amd64/motif12/libmawt.so
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1650)
        at java.lang.Runtime.load0(Runtime.java:770)
        at java.lang.System.load(System.java:1005)
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1668)
        at java.lang.Runtime.loadLibrary0(Runtime.java:823)
        at java.lang.System.loadLibrary(System.java:1030)
        at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:50)
        at java.security.AccessController.doPrivileged(Native Method)
        at sun.awt.NativeLibLoader.loadLibraries(NativeLibLoader.java:38)
        at sun.awt.DebugHelper.<clinit>(DebugHelper.java:29)
        at java.awt.Component.<clinit>(Component.java:552)
        at javax.swing.ImageIcon.<clinit>(ImageIcon.java:61)
        at com.mathworks.mwswing.desk.Desktop.<clinit>(Desktop.java:103)
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Class.java:169)
        at com.mathworks.jmi.OpaqueJavaInterface.findClass(OpaqueJavaInterface.java:470)
 Failed to start the Desktop: Failure loading desktop class

```
I assume this is because I couldn't go through the wiki's insctructions (are they redefining the classes there?). Could you please help me here, as I need Matlab for my studies and the only thing standing between me and a running Matlab is this annoying Java bug...
Thanks a lot in advance, 

Bastian

---

### Post by cherry316316 on 2007-10-31
> **Buzzdee said:**
> Well, maybe someone can help me then:
I'm running Gutsy 64bit on a lenovo T61p with the restricted NVidia drivers and compiz enabled. I get the very popular blank-screen-in-java-apps problem and found some tips on where to add the following:
```
export MATLAB_JAVA=/usr/lib/jvm/java-6-sun/jre && matlab
Unable to initialize com.mathworks.mwswing.MJStartup
java.lang.UnsatisfiedLinkError: Can't load library: /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/amd64/motif12/libmawt.so
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1650)
        at java.lang.Runtime.load0(Runtime.java:770)
        at java.lang.System.load(System.java:1005)
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1668)
        at java.lang.Runtime.loadLibrary0(Runtime.java:823)
        at java.lang.System.loadLibrary(System.java:1030)
        at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:50)
        at java.security.AccessController.doPrivileged(Native Method)
        at sun.awt.NativeLibLoader.loadLibraries(NativeLibLoader.java:38)
        at sun.awt.DebugHelper.<clinit>(DebugHelper.java:29)
        at java.awt.Component.<clinit>(Component.java:552)
        at javax.swing.ImageIcon.<clinit>(ImageIcon.java:61)
        at com.mathworks.mwswing.desk.Desktop.<clinit>(Desktop.java:103)
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Class.java:169)
        at com.mathworks.jmi.OpaqueJavaInterface.findClass(OpaqueJavaInterface.java:470)
 Failed to start the Desktop: Failure loading desktop class

```
I assume this is because I couldn't go through the wiki's insctructions (are they redefining the classes there?). Could you please help me here, as I need Matlab for my studies and the only thing standing between me and a running Matlab is this annoying Java bug...
Thanks a lot in advance, 

Bastian


check this forum
[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=467133](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=467133)

---

### Post by bfeero on 2007-11-07
Buzzdee, did you get things to work?  I am having the same problem.  I am trying to run Matlab R2007b.

I have added the following "export" lines to the matlab run file:
```

#!/bin/sh
export AWT_TOOLKIT=MToolkit
export MATLAB_JAVA=/usr/lib/jvm/java-6-sun/jre/
#
#  Name:
#     matlab    script file for invoking MATLAB
#
#  Usage:
#     matlab [-h|-help] | [-n | -e]
#

```

When I run matlab from the command line, I get this error, very similar to Buzzdee's:

```
Unable to initialize com.mathworks.mwswing.MJStartup
java.lang.UnsatisfiedLinkError: Can't load library: /usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib/amd64/motif12/libmawt.so
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1650)
        at java.lang.Runtime.load0(Runtime.java:770)
        at java.lang.System.load(System.java:1005)
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1668)
        at java.lang.Runtime.loadLibrary0(Runtime.java:823)
        at java.lang.System.loadLibrary(System.java:1030)
        at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:50)
        at java.security.AccessController.doPrivileged(Native Method)
        at sun.awt.NativeLibLoader.loadLibraries(NativeLibLoader.java:38)
        at sun.awt.DebugHelper.<clinit>(DebugHelper.java:29)
        at java.awt.Component.<clinit>(Component.java:552)
        at javax.swing.ImageIcon.<clinit>(ImageIcon.java:61)
        at com.mathworks.mwswing.desk.Desktop.<clinit>(Desktop.java:103)
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Class.java:169)
        at com.mathworks.jmi.OpaqueJavaInterface.findClass(OpaqueJavaInterface.java:470)
 Failed to start the Desktop: Failure loading desktop class

```

I'm not sure what I'm doing wrong.  I've check the other post referenced by cherry, but I'm unable to find a solution.  It's probably something really simple and stupid.

bfeero

EDIT:  solution found

OK, yes, it was something stupid.  In the other forum, someone suggested commenting out the "first line."  For me, that is

```

export AWT_TOOLKIT=MToolkit

```

If I delete (or uncomment) that line, everything works perfectly!  Yes!

bfeero

---

### Post by Buddy Gurt on 2007-11-09
I had the same Matlab - Compiz problem, but I could solve it thanks to you guys.

I installed sun-java6-jre first, and then added
```
export MATLAB_JAVA=/usr/lib/jvm/java-6-sun/jre/
```
right at the beginning (after #!/bin/sh) of the file 'matlabroot$/bin/matlab'...

Problem solved!

---

### Post by Series8217 on 2007-11-28
Buddy Gurt's solution worked for me as well.

---

### Post by Claus7 on 2007-11-29
Hello,

I'm using matlab R2007b and the aforementioned command works to me too if I type it in terminal. Yet, I have to type it every time I open my pc. I haven't found a way to insert it in any /matlab/bin file because every time I get errors. Other than that it works fine. 

I see also that Beryl and compiz have merged and that in synaptic compiz is chosen by default. In addition I cannot find in this version of matlab a startup.m file in which I could add the aforementioned command. Something similar that I found is startupsav.m at /usr/local/matlab/toolbox/local
Any suggestions?

Regards!

---

### Post by Claus7 on 2007-11-29
Hello,

problem solved! I went in .bashrc and I typed :
```
alias matlab="export MATLAB_JAVA=/usr/lib/jvm/java-6-sun/jre/ && matlab"
```

I RESTARTED in order for the change to take effect and every time I invoke matlab, it is just as it should be.

Regards!

---

### Post by markkiteflyer on 2008-01-24
Hi,
Thank you for the help. This solved the problem for me.
I only needed to add the export command to the start of the matlab file.  I didn't need any of the wiki page instructions (which was just as well as the page is missing).

I found the easiest way was to edit */usr/local/matlab2007b/bin/matlab* which is the target of the link */usr/bin/matlab*, or what I get from
```
$> ls -l `which matlab`
```
Just adding
```
export MATLAB_JAVA='/usr/lib/jvm/java-6-sun/jre/
```
at the top so that it reads:
```
#!/bin/sh
export MATLAB_JAVA=/usr/lib/jvm/java-6-sun/jre/
#
#  Name:
#     matlab    script file for invoking MATLAB
#
#  Usage:
#     matlab [-h|-help] | [-n | -e]

```
was all it took to work perfectly.

---

### Post by musicinmybrain on 2008-01-24
Fantastic! This solved my problem as well.

---

### Post by JudgeFudge on 2008-01-25
I added /usr/local/bin/matlab which looks like:

export MATLAB_JAVA=/opt/java/jdk1.6.0_04/jre
/opt/matlab/bin/matlab

and it now works. I installed the JDK from Sun, if anyone else does this you need to make sure you add the "jre" at the end of the export. I didn't originally (since I was just adding JAVA_HOME) and it took me to the command line version of matlab.

---

### Post by tribaal on 2008-01-25
I worked around this bug by exporting AWT_TOOLKIT=MToolkit before running my java program:

```
export AWT_TOOLKIT=MToolkit
```

I didn't even need to install Java 6 (my work project has to work on Java 1.5).

So far I didn't find any problems, maybe mathlab works in a particular way?

Hope this helps :)

- Trib'

---

### Post by firestormx37 on 2008-01-28
Thanks a lot!  This worked for me.

---

### Post by Adman on 2008-03-27
Thanks Buddy Gurt, Solution worked for me as well..

---

