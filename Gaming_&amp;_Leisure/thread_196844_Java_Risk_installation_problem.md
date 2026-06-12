---
title: "Java Risk installation problem"
date: 2006-06-14
forum: Gaming &amp; Leisure
---

### Post by nalmeth on 2006-06-14
Trying to install Java Risk, but getting nowhere
```
sdcb@vaiobuntu:~/Packages$ java -jar Risk_install_1.0.8.7.jar
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.7)
   at java.awt.Font.tk(libgcj.so.7)
   at java.awt.Font.getPeerFromToolkit(libgcj.so.7)
   at java.awt.Font.<init>(libgcj.so.7)
   at javax.swing.plaf.FontUIResource.<init>(libgcj.so.7)
   at javax.swing.plaf.metal.DefaultMetalTheme.<clinit>(libgcj.so.7)
   at java.lang.Class.initializeClass(libgcj.so.7)
   at javax.swing.plaf.metal.MetalLookAndFeel.createDefaultTheme(libgcj.so.7)
   at javax.swing.plaf.metal.MetalLookAndFeel.<init>(libgcj.so.7)
   at javax.swing.UIManager.<clinit>(libgcj.so.7)
   at java.lang.Class.initializeClass(libgcj.so.7)
   at com.izforge.izpack.installer.GUIInstaller.loadLookAndFeel(GUIInstaller.java:272)
   at com.izforge.izpack.installer.GUIInstaller.<init>(GUIInstaller.java:114)
   at java.lang.Class.newInstance(libgcj.so.7)
   at com.izforge.izpack.installer.Installer.main(Installer.java:62)
Caused by: java.lang.ClassNotFoundException: gnu.java.awt.peer.gtk.GtkToolkit
   at java.lang.Class.forName(libgcj.so.7)
   at java.lang.Class.forName(libgcj.so.7)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.7)
   ...14 more
```
I'm pretty sure I have Sun Java 1.5 JRE installed, should be more than enough to run this (JRE 1.4 is only requirement), am I missing something?

---

### Post by Nequeo on 2006-06-14
[QUOTE=nalmeth]Trying to install Java Risk, but getting nowhere
```
sdcb@vaiobuntu:~/Packages$ java -jar Risk_install_1.0.8.7.jar
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.7)
   at java.awt.Font.tk(libgcj.so.7)
   at java.awt.Font.getPeerFromToolkit(libgcj.so.7)
   at java.awt.Font.<init>(libgcj.so.7)
   at javax.swing.plaf.FontUIResource.<init>(libgcj.so.7)
   at javax.swing.plaf.metal.DefaultMetalTheme.<clinit>(libgcj.so.7)
   at java.lang.Class.initializeClass(libgcj.so.7)
   at javax.swing.plaf.metal.MetalLookAndFeel.createDefaultTheme(libgcj.so.7)
   at javax.swing.plaf.metal.MetalLookAndFeel.<init>(libgcj.so.7)
   at javax.swing.UIManager.<clinit>(libgcj.so.7)
   at java.lang.Class.initializeClass(libgcj.so.7)
   at com.izforge.izpack.installer.GUIInstaller.loadLookAndFeel(GUIInstaller.java:272)
   at com.izforge.izpack.installer.GUIInstaller.<init>(GUIInstaller.java:114)
   at java.lang.Class.newInstance(libgcj.so.7)
   at com.izforge.izpack.installer.Installer.main(Installer.java:62)
Caused by: java.lang.ClassNotFoundException: gnu.java.awt.peer.gtk.GtkToolkit
   at java.lang.Class.forName(libgcj.so.7)
   at java.lang.Class.forName(libgcj.so.7)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.7)
   ...14 more
```
I'm pretty sure I have Sun Java 1.5 JRE installed, should be more than enough to run this (JRE 1.4 is only requirement), am I missing something?[/QUOTE]


You'll probably need to type 'sudo update-alternatives --config java' from the command line first.

Give that a shot and see if it helps any.

---

### Post by nalmeth on 2006-06-14
Thanks for help:
```
sdcb@vaiobuntu:~/Packages$ sudo update-alternatives --config java
Password:

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.1
      2        /usr/bin/gij-wrapper-4.0
*+    3        /usr/lib/jvm/java-gcj/jre/bin/java
```
I've got the right one already don't I?

---

### Post by Bokonon on 2006-06-15
Looks good to me.

---

### Post by nalmeth on 2006-06-15
Turns out it did install the game, I found the executable in /usr/games

I think there is still something wrong though. The game seems broken or something. First try, I set everything up, and the AI guys never make their move. I'm stuck waiting for the first move, and can't do anything

"Wait your turn'
"It's player2's turn"

Then when trying again, I can't even set the map up.

Anyone else having Java Risk problems? The game looks SWEET I want to be able to play properly.

---

