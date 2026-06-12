---
title: "File Menu disappears in Matlab with Beryl"
date: 2007-10-03
forum: Desktop Effects &amp; Customization
---

### Post by zksailor534 on 2007-10-03
When using MATLAB while running Beryl, all the File, Edit, etc menus and toolbars at the top of the command window are invisible.  They're still usable if I can guess where they are, but not visible.  This would be workable, except that it's not the only problem: anything inside the Editor window is completely invisible, including menus, toolbars, and the text of any actual file.  Any ideas would be quite helpful since I've already tried any other workarounds mentioned in other matlab posts.  I'm running Feisty on AMD64 with linux-native Matlab R2007a.

---

### Post by maloo on 2007-10-04
Hi,

I've just installed 2007a and had the same problem.  Using "export AWT_TOOLKIT=MToolkit" at the start of the matlab script fixed this for me thou. 
I also have "export MATLAB_JAVA=/usr/lib/jvm/java-6-sun-1.6.0.00/jre" since the java that came with matlab cause simulink to crash.

other stuff.... Kubuntu 7.04 (32bit), beryl (with nvidia drivers if i remember correctly)

hope this helps....
Paul

---

### Post by zksailor534 on 2007-10-06
Just upgraded to Matlab R2007b and the fix does not work.  In fact, the entire interior of the Matlab window is now invisible, I no longer even have a command window.

---

### Post by Pedro Huerta on 2007-10-11
I'm using Matlab R2007b in Ubuntu Feisty. It worked for me after exporting:
```
export AWT_TOOLKIT=MToolkit
```.

Good luck.

---

### Post by Pedro Huerta on 2007-10-11
> **Pedro Huerta said:**
> I'm using Matlab R2007b in Ubuntu Feisty. It worked for me after exporting:
```
export AWT_TOOLKIT=MToolkit
```.

Good luck.

But... I can only launch it from a console. Any ideas?

---

### Post by Pedro Huerta on 2007-10-12
Ok, got it. Just needed to:
1. Add the following line (before the first uncommented one) to Matlabdir/bin/matlab  ```
export AWT_TOOLKIT=MToolkit
``` to  
2. Launch matlab ```
matlab -desktop
```. It runs from the Launch app menu (Alt+F2).
Everything is working.

---

### Post by zksailor534 on 2008-02-13
Sorry to resurrect this old thread, but I still have the same problem.  I've been running Matlab with the -nodesktop option since I haven't had time to fix it.  With both export options in the matlab program file, this is the error I receive:
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

There is no such thing as a motif12 folder in that directory, but there is motif21.  I've tried creating a symbolic link between those two without any success.

---

### Post by aquamammal on 2008-02-19
Hey thanks man. That solved my problem.

---

### Post by Bungler on 2008-03-04
I had the same problem, but I found a different solution on the net:

Matlab uses its own JRE to viualize the menu's. However you can also use JRE from your own specified place. You have to have JRE installed of course. I have version 1.6 installed and in this version Matlab works fine.

You can just add an export command referring to you JRE environment in the matlab.sh file.
You should specify the folder which contains the file "rt.jar", but than one folder level up. So in my case the "rt.jar" file is in the folder:

/usr/lib/jvm/java-6-sun-1.6.0.03/jre/lib, so I have to use:

/usr/lib/jvm/java-6-sun-1.6.0.03/jre

The command to be added on the first uncommented line becomes (in my case):

export MATLAB_JAVA=/usr/lib/jvm/java-6-sun-1.6.0.03/jre


good luck!

---

### Post by sungohan on 2008-07-06
> **maloo said:**
> Hi,

I've just installed 2007a and had the same problem.  Using "export AWT_TOOLKIT=MToolkit" at the start of the matlab script fixed this for me thou. 
I also have "export MATLAB_JAVA=/usr/lib/jvm/java-6-sun-1.6.0.00/jre" since the java that came with matlab cause simulink to crash.

other stuff.... Kubuntu 7.04 (32bit), beryl (with nvidia drivers if i remember correctly)

hope this helps....
Paul

Thanks man, this solved my problem.
I must put "AWT_TOOLKIT=MToolkit" at the beginning of the script, 
putting it at the end does not work.

---

