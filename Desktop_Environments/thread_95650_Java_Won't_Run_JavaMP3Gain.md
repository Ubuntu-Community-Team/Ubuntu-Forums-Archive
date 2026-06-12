---
title: "Java Won't Run JavaMP3Gain"
date: 2005-11-27
forum: Desktop Environments
---

### Post by palsyboy on 2005-11-27
I followed the [Offical Ubuntu FAQ Guide]("http://help.ubuntu.com/starterguide/C/faqguide-all.html#sect-java") to set up my JRE for Breezy, and it seemed to go fine.  I'd been using the same version [number unknown] of JavaMP3Gain for at least four or five months now with no problems on Hoary, but now I get this error:
```

palsyboy@giedi-prime:~$ java -jar /opt/javamp3gain/JavaMP3Gain.jar
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit() (/usr/lib/libgcj.so.6.0.0)
   at java.awt.EventQueue.invokeLater(java.lang.Runnable) (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.SwingUtilities.invokeLater(java.lang.Runnable) (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.RepaintManager.addInvalidComponent(javax.swing.JComponent) (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.JComponent.revalidate() (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.JComponent.setOpaque(boolean) (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.JPanel.JPanel(java.awt.LayoutManager, boolean) (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.JPanel.JPanel() (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.JRootPane.createGlassPane() (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.JRootPane.getGlassPane() (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.JRootPane.JRootPane() (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.JFrame.createRootPane() (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.JFrame.getRootPane() (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.JFrame.frameInit() (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.JFrame.JFrame() (/usr/lib/libgcj.so.6.0.0)
   at JavaMP3Gain.JavaMP3Gain() (Unknown Source)
   at JavaMP3Gain.main(java.lang.String[]) (Unknown Source)
   at gnu.java.lang.MainThread.call_main() (/usr/lib/libgcj.so.6.0.0)
   at gnu.java.lang.MainThread.run() (/usr/lib/libgcj.so.6.0.0)
Caused by: java.lang.ClassNotFoundException: gnu.java.awt.peer.gtk.GtkToolkit not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:/opt/javamp3gain/JavaMP3Gain.jar,file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.ClassLoader.loadClass(java.lang.String, boolean) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.forName(java.lang.String, boolean, java.lang.ClassLoader) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.forName(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.awt.Toolkit.getDefaultToolkit() (/usr/lib/libgcj.so.6.0.0)
   ...18 more
```

Does anyone know what that means?  Thanks for any help you can provide.

---

### Post by Leif on 2005-11-27
the error messages you're getting show that you're still using gcj, and not sun's jre. I'm sure this is fixable from this point on, but I don't know how. I do know that this worked for me though : [https://wiki.ubuntu.com/forum/software/JavaApt](https://wiki.ubuntu.com/forum/software/JavaApt)

---

### Post by palsyboy on 2005-12-01
Sorry about the late reply.

Thank you for the input, but I get the exact same error (to the letter).  I don't know why this is giving me so many problems this time around when it worked just fine for Hoary. :confused:

---

### Post by akiro.yamamoto on 2005-12-01
You seem to be using the free java verion.
You need to run this code and select the correct java version:
CODE:
sudo update-alternatives --config java

I think it's selection number 3, at least that's what it is on my system.
Hope that helps

---

### Post by palsyboy on 2005-12-05
That worked like a charm.  Thank you immensely! :D

---

### Post by cvmostert on 2005-12-18
[QUOTE=palsyboy]That worked like a charm.  Thank you immensely! :D[/QUOTE]
:p 
ahhhh! fantastic! it worked for me aswell...

i had to choose option 1

---

