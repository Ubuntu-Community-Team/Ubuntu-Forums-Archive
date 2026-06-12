---
title: "DVD Authoring"
date: 2005-11-17
forum: Desktop Environments
---

### Post by ColinG on 2005-11-17
What software are people using to author dvd's? I've prepared a dvd on KIno but now neeed to author it with some menues/chapters.

Thanks

---

### Post by kingsidy on 2005-11-17
i think that QDVDAuthor does that.

---

### Post by ColinG on 2005-11-17
I've tried that but could not get it to work. At least K3b would not burn the resulting image.:(

---

### Post by kingsidy on 2005-11-17
you can try  DVDStyler. I personnally used use varsha when making dvd from video i download, but i do not know whether you can get chapters with it.

---

### Post by ColinG on 2005-11-17
[QUOTE=kingsidy]you can try  DVDStyler. I personnally used use varsha when making dvd from video i download, but i do not know whether you can get chapters with it.[/QUOTE]

I'll give it a try. Many thanks.

Did you get any problems getting k3b to burn the dvd. I keep getting errors such as can't define file length. And when it does burn it does not erase the previous data on a DVD RW disc

---

### Post by kingsidy on 2005-11-17
I burn dvd iso's fine with k3b. although i use nerolinux most of the time.

---

### Post by shibub on 2005-12-13
[QUOTE=kingsidy]you can try  DVDStyler. I personnally used use varsha when making dvd from video i download, but i do not know whether you can get chapters with it.[/QUOTE]

I could not find DVDStyler or varsha in Synaptic.  Do I need to build them manually?

---

### Post by ColinG on 2005-12-14
[QUOTE=shibub]I could not find DVDStyler or varsha in Synaptic.  Do I need to build them manually?[/QUOTE]

Varsha is a java applet so download and unpack it. DVDStyler you will have to compile if you can't find it on the repositories. The last time I tried it it was broken due to an issue with mjpegtools. DVDauthorwizard is worth a try though, that certainly works, I tried vesrion 1.0  last night, although these days I'm using SuSe 10 so I can't speak for Ubuntu.

---

### Post by cvmostert on 2005-12-18
[QUOTE=kingsidy]you can try  DVDStyler. I personnally used use varsha when making dvd from video i download, but i do not know whether you can get chapters with it.[/QUOTE]

i tried to download varsha at the original site, and cannot seem to download the file, are there any mirror sites?

thanks

---

### Post by xvolks on 2005-12-18
I can download it from [http://prdownloads.sourceforge.net/varsha/varsha.jar?download](http://prdownloads.sourceforge.net/varsha/varsha.jar?download)

Hope this help you...

---

### Post by cvmostert on 2005-12-18
Thank you...

Ok i got to download varsha, but now java does not want to run it... 
i type java -jar varsha.jar and it stalls for a while and outputs this:

> Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
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
   at varsha.ui.Varsha.Varsha() (Unknown Source)
   at varsha.ui.Varsha.main(java.lang.String[]) (Unknown Source)
   at gnu.java.lang.MainThread.call_main() (/usr/lib/libgcj.so.6.0.0)
   at gnu.java.lang.MainThread.run() (/usr/lib/libgcj.so.6.0.0)
Caused by: java.lang.ClassNotFoundException: gnu.java.awt.peer.gtk.GtkToolkit not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:/home/chris/varsha/varsha.jar,file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.ClassLoader.loadClass(java.lang.String, boolean) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.forName(java.lang.String, boolean, java.lang.ClassLoader) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.forName(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.awt.Toolkit.getDefaultToolkit() (/usr/lib/libgcj.so.6.0.0)
   ...18 more


what could be wrong?

---

### Post by cvmostert on 2005-12-19
got the problem, i was using the wrong java.... had do change some settings... do use sun's java when i use the command "java"

---

### Post by Dr Gonzo on 2006-01-14
There's also a really good DVD authoring HOWTO on the Gentoo forums [here.]("http://forums.gentoo.org/viewtopic-t-117709-highlight-dvd+authoring+howto.html")

---

### Post by cvmostert on 2006-01-15
thanx, will have a look.

---

