---
title: "DrJava launching problem"
date: 2006-02-23
forum: Desktop Environments
---

### Post by FIONEX on 2006-02-23
Hey,
When I type the command $ java -jar drjava.jar, i get the following error
```

 java -jar drjava.jar
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit() (/usr/lib/libgcj.so.6.0.0)
   at java.awt.Font.tk() (/usr/lib/libgcj.so.6.0.0)
   at java.awt.Font.getFontFromToolkit(java.lang.String, java.util.Map) (/usr/lib/libgcj.so.6.0.0)
   at java.awt.Font.decode(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at edu.rice.cs.drjava.config.OptionConstants$DefaultFont.getDefaultMainFont() (Unknown Source)
   at edu.rice.cs.drjava.config.OptionConstants.<clinit>() (Unknown Source)
   at java.lang.Class.initializeClass() (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.forName(java.lang.String, boolean, java.lang.ClassLoader) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.forName(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at com.rc.retroweaver.runtime.ClassLiteral.getClass(java.lang.String) (Unknown Source)
   at edu.rice.cs.drjava.config.OptionMapLoader.<clinit>() (Unknown Source)
   at java.lang.Class.initializeClass() (/usr/lib/libgcj.so.6.0.0)
   at edu.rice.cs.drjava.config.SavableConfiguration.loadConfiguration(java.io.InputStream) (Unknown Source)
   at edu.rice.cs.drjava.config.FileConfiguration.loadConfiguration() (Unknown Source)
   at edu.rice.cs.drjava.DrJava._initConfig() (Unknown Source)
   at edu.rice.cs.drjava.DrJava.<clinit>() (Unknown Source)
   at java.lang.Class.initializeClass() (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.forName(java.lang.String, boolean, java.lang.ClassLoader) (/usr/lib/libgcj.so.6.0.0)
   at gnu.java.lang.MainThread.run() (/usr/lib/libgcj.so.6.0.0)
Caused by: java.lang.ClassNotFoundException: gnu.java.awt.peer.gtk.GtkToolkit not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:drjava.jar,file:./], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.ClassLoader.loadClass(java.lang.String, boolean) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.forName(java.lang.String, boolean, java.lang.ClassLoader) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.forName(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.awt.Toolkit.getDefaultToolkit() (/usr/lib/libgcj.so.6.0.0)
   ...18 more

```
Any ideas?  Am I missing GTK?

---

### Post by FIONEX on 2006-02-23
Turns out the problem has to do with the gcj library distributed with ubuntu.  What you have to do is download and install j2re from sun microsystems and then do the following:
```

$ sudo update-alternatives --config java

```

Then choose the proper one from the list, being sun's j2re.  That problem is apparantly due to the switch over from java 1.4.2 to 1.5.0+.

I hope this contribution helps someone out.  If not, I'm putting it here as a reference for myself!

---

