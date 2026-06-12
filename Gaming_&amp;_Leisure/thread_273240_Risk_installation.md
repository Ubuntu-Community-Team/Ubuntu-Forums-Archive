---
title: "Risk installation?"
date: 2006-10-07
forum: Gaming &amp; Leisure
---

### Post by haxer on 2006-10-07
Hello ive downloaded risk and its a .jar file how to install it?

---

### Post by henriquemaia on 2006-10-08
You don't need to install it. You must have java installed and then, on a terminal, type:

```
java -jar name_of_the_jar_game.jar
```

---

### Post by jdunn on 2006-10-08
My output:
```

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
   at com.izforge.izpack.installer.GUIInstaller.loadLookAndFeel(GUIInstaller.java:299)
   at com.izforge.izpack.installer.GUIInstaller.<init>(GUIInstaller.java:119)
   at java.lang.Class.newInstance(libgcj.so.7)
   at com.izforge.izpack.installer.Installer.main(Installer.java:62)
Caused by: java.lang.ClassNotFoundException: gnu.java.awt.peer.gtk.GtkToolkit
   at java.lang.Class.forName(libgcj.so.7)
   at java.lang.Class.forName(libgcj.so.7)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.7)

```

I have sun java JRE installed.  Do I need the JDK as well?  I'm running Kubuntu.  If it means I'm missing GTK libraries (or something like that) I don't know which package I need.

---

### Post by jdunn on 2006-10-08
Okay, I figured out that I needed the awt library, which I installed from the repositories.  Now when I run Risk, I get no error messages in the commandline but the game doesn't run.  :-k

---

### Post by henriquemaia on 2006-10-08
I have tried running risk myself and it runs ok. Maybe you're missing some library. I also have java SKD, but don't know if it's related.

---

### Post by jdunn on 2006-10-08
All I get is this, which is typical for any application that I run from the terminal in KDE:

```

~/Games/risk$ java -jar Risk_install_1.0.8.8.jar
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

```

No game window pops up.

---

### Post by bastiegast on 2006-10-08
You might have sun java installed, but not using it. It seems like your program is executed with gcj. You can force ubuntu to use sun java by removing gcj(what i did), you may need to reinstall sun java then. Theres also a cleaner command to make ubuntu use the right java, but i cant remember it.

---

### Post by jdunn on 2006-10-08
> **bastiegast said:**
> You might have sun java installed, but not using it. It seems like your program is executed with gcj. You can force ubuntu to use sun java by removing gcj(what i did), you may need to reinstall sun java then. Theres also a cleaner command to make ubuntu use the right java, but i cant remember it.

I forgot about that.  I remembered this web page which did the trick:
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by haxer on 2006-10-08
I get this out put oem@haxer:~$ java -jar Risk_install_1.0.8.6.jar
Unable to access jarfile Risk_install_1.0.8.6.jar

---

