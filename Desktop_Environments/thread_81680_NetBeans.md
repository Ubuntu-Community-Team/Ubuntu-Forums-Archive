---
title: "NetBeans"
date: 2005-10-24
forum: Desktop Environments
---

### Post by rj686 on 2005-10-24
I got the binary for j2sdk and j2rel installed fine(in usr/local/) and i got netbeans installed fine but when i try to run it, it wont run. i searched for thef ile and clicked run in terminal but the error goes away too fast for me to see it. Can someone help me?

---

### Post by coldrick on 2005-10-24
If you installed properly, you should have an icon for netBeans on your desktop.

Take a look at [http://blogs.sun.com/roller/page/coldrick](http://blogs.sun.com/roller/page/coldrick) for detailed instructions.

Regards,
David

---

### Post by rj686 on 2005-10-24
i do have a netbeans icon i just get an error when i try to run it. Thx ill try that real quick.........

bXp.so.6: cannot open shared object file: No such file or directory
        at java.lang.ClassLoader$NativeLibrary.load(Native Method)
        at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1586)
        at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1503)
        at java.lang.Runtime.loadLibrary0(Runtime.java:788)
        at java.lang.System.loadLibrary(System.java:834)
        at sun.security.action.LoadLibraryAction.run(LoadLibraryAction.java:50)
        at java.security.AccessController.doPrivileged(Native Method)
        at java.awt.Toolkit.loadLibraries(Toolkit.java:1437)
        at java.awt.Toolkit.<clinit>(Toolkit.java:1458)
        at java.awt.Color.<clinit>(Color.java:250)
        at javax.swing.plaf.metal.MetalTheme.<clinit>(MetalTheme.java:32)
        at javax.swing.plaf.metal.MetalLookAndFeel.getCurrentTheme(MetalLookAndFeel.java:1294)
        at javax.swing.plaf.metal.MetalLookAndFeel.createDefaultTheme(MetalLookAndFeel.java:1226)
        at javax.swing.plaf.metal.MetalLookAndFeel.getDefaults(MetalLookAndFeel.java:1233)
        at javax.swing.UIManager.setLookAndFeel(UIManager.java:394)
        at javax.swing.UIManager.setLookAndFeel(UIManager.java:424)
        at javax.swing.UIManager.initializeDefaultLAF(UIManager.java:1085)
        at javax.swing.UIManager.initialize(UIManager.java:1181)
        at javax.swing.UIManager.maybeInitialize(UIManager.java:1164)
        at javax.swing.UIManager.getDefaults(UIManager.java:480)
        at javax.swing.UIManager.getString(UIManager.java:583)
        at javax.swing.filechooser.UnixFileSystemView.<clinit>(FileSystemView.java:537)
        at javax.swing.filechooser.FileSystemView.getFileSystemView(FileSystemView.java:68)
        at org.openide.filesystems.FileUtil.<clinit>(FileUtil.java:49)
        at org.netbeans.core.NonGui.getUserDir(NonGui.java:118)
        at org.netbeans.core.NonGui.getLogDir(NonGui.java:147)
        at org.netbeans.core.CLIOptions.initialize(CLIOptions.java:192)
        at org.netbeans.core.Main.start(Main.java:304)
        at org.netbeans.core.TopThreadGroup.run(TopThreadGroup.java:90)
        at java.lang.Thread.run(Thread.java:534)

---

### Post by coldrick on 2005-10-24
make sure you have Java installed correctly - in particular, if you type into a terminal:

java -version

you should get something like

java version "1.5.0_05"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_05-b05)
Java HotSpot(TM) Client VM (build 1.5.0_05-b05, mixed mode, sharing)

Regards,
David

---

### Post by rj686 on 2005-10-24
java version "1.5.0_04"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_04-b05)
Java HotSpot(TM) Client VM (build 1.5.0_04-b05, mixed mode, sharing)


thats what it printed out but tahts not the jdk im using

i just installed 5.0 beta........but it didnt put a link on my desktop
I located the file hit "Run in terminal" it opened up a terminal and then closed it

---

### Post by coldrick on 2005-10-24
Don't understand - what jdk **are** you using?

Regards,
David

---

### Post by rj686 on 2005-10-25
j2sdk 1.4.2
do you have aim/gaim? my name is the same as my s/n for the froums.....that might b faster let me know if u get on

---

### Post by coldrick on 2005-10-25
I suspect that you're using libgcj6, which is probably not a complete Java release. Take a look thru [http://blogs.sun.com/roller/page/coldrick?entry=java_development_on_ubuntu_part](http://blogs.sun.com/roller/page/coldrick?entry=java_development_on_ubuntu_part) to make sure you've installed and set up java properly.

Sorry, I'm not on im . . .

Regards,
David

---

### Post by rj686 on 2005-10-25
thx for teh advice..ill hafta try it tomorrow after school...just a question, does limewire require jdk? because limewire works on my computer, and azureus does too(both of which i heard are java programs). One more question, in your opinion how does solaris compare to linux in terms of games/development enviornment/media?

---

### Post by coldrick on 2005-10-25
They probably don't require the jdk, just the jre (runtime).

Regards,
David

---

### Post by rj686 on 2005-10-25
when i get the chance should i remove libgcj6?

---

### Post by coldrick on 2005-10-25
I wouldn't - for some strange reason a lot of packages (like nvidia!) have dependency on it: why, I dunno.

I don't know why this package is included: it isn't a proper, complete version of Java.

---

### Post by rj686 on 2005-10-25
hmmm, ill take a look tomorrow, like i said thx for the help man :).....what about Solaris (gaming/development/media). I noticed on ur blog u work for sun so im sure you've at least tried it.

---

### Post by bryan986 on 2005-10-25
Try the java 1.5 sdk with netbeans 4.1 bundle package, thats what I usually do...I just install it and it works...

---

