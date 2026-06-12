---
title: "java and .jar"
date: 2005-11-06
forum: Desktop Environments
---

### Post by drguitarum2005 on 2005-11-06
I tried to open a .jar file with $java -jar file.jar and this is my output:  

```
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit() (/usr/lib/libgcj.so.6.0.0)
   at java.awt.Font.tk() (/usr/lib/libgcj.so.6.0.0)
   at java.awt.Font.getPeerFromToolkit(java.lang.String, java.util.Map) (/usr/lib/libgcj.so.6.0.0)
   at java.awt.Font.Font(java.lang.String, int, int) (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.plaf.FontUIResource.FontUIResource(java.lang.String, int, int) (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.plaf.metal.DefaultMetalTheme.<clinit>() (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.initializeClass() (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.plaf.metal.MetalLookAndFeel.createDefaultTheme() (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.plaf.metal.MetalLookAndFeel.MetalLookAndFeel() (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.UIManager.<clinit>() (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.initializeClass() (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.UIManager.getUI(javax.swing.JComponent) (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.JLabel.updateUI() (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.JLabel.JLabel(java.lang.String, javax.swing.Icon, int) (/usr/lib/libgcj.so.6.0.0)
   at javax.swing.JLabel.JLabel(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at itunes.client.swing.One2OhMyGod.One2OhMyGod() (Unknown Source)
   at itunes.client.swing.One2OhMyGod.main(java.lang.String[]) (Unknown Source)
   at gnu.java.lang.MainThread.call_main() (/usr/lib/libgcj.so.6.0.0)
   at gnu.java.lang.MainThread.run() (/usr/lib/libgcj.so.6.0.0)
Caused by: java.lang.ClassNotFoundException: gnu.java.awt.peer.gtk.GtkToolkit not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:OT44src.jar,file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.ClassLoader.loadClass(java.lang.String, boolean) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.forName(java.lang.String, boolean, java.lang.ClassLoader) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.forName(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.awt.Toolkit.getDefaultToolkit() (/usr/lib/libgcj.so.6.0.0)
   ...18 more

```

does anyone know that all that means and what I can do to fix this? thanks,

---

### Post by RAOF on 2005-11-06
Either you need to install a Java runtime (I like the sun java runtime.  Nice and official), or you need to properly set up your existing runtime.

Follow this [howto]("http://www.ubuntuforums.org/showthread.php?t=76735&highlight=java+package+1.5") to install & set up the sun java runtime.  It was written for the previous version (Hoary) but the same steps still work for Breezy.

---

### Post by jvictor on 2005-11-07
Please stick to Sun Java if u r doing some real development. Things look pretty wierd to me in GNU java, many things dont work the way it has to

---

