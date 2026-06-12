---
title: "Java + Firefox: unable to load facebook applet"
date: 2010-06-24
forum: Desktop Environments
---

### Post by manolomanolo on 2010-06-24
Hi to all.

I am trying to execute the Java applet to load photos but I am unable to open it. This is what I get when running firefox from terminal

```
mano@mano-laptop:~$ firefox &
[1] 7632
mano@mano-laptop:~$ java version "1.6.0_18"
OpenJDK Runtime Environment (IcedTea6 1.8) (6b18-1.8-0ubuntu1)
OpenJDK 64-Bit Server VM (build 14.0-b16, mixed mode)
java.lang.InterruptedException: sleep interrupted
	at java.lang.Thread.sleep(Native Method)
	at sun.applet.PluginAppletViewer.handleMessage(PluginAppletViewer.java:735)
	at sun.applet.PluginAppletViewer.handleMessage(PluginAppletViewer.java:649)
	at sun.applet.PluginStreamHandler.handleMessage(PluginStreamHandler.java:270)
	at sun.applet.PluginMessageHandlerWorker.run(PluginMessageHandlerWorker.java:82)
Facebook Photo Uploader 5 version: 5.5.8.0
Current document URL: http://www.facebook.com/home.php?#!/
java.lang.NoClassDefFoundError: IllegalName: <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
	at java.lang.ClassLoader.preDefineClass(ClassLoader.java:491)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:628)
	at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:142)
	at java.net.URLClassLoader.defineClass(URLClassLoader.java:277)
	at java.net.URLClassLoader.access$000(URLClassLoader.java:73)
	at java.net.URLClassLoader$1.run(URLClassLoader.java:212)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at net.sourceforge.jnlp.runtime.JNLPClassLoader.findClass(JNLPClassLoader.java:887)
	at net.sourceforge.jnlp.runtime.JNLPClassLoader.loadClassExt(JNLPClassLoader.java:909)
	at net.sourceforge.jnlp.runtime.JNLPClassLoader.loadClass(JNLPClassLoader.java:824)
	at javax.xml.parsers.FactoryFinder.getProviderClass(FactoryFinder.java:113)
	at javax.xml.parsers.FactoryFinder.newInstance(FactoryFinder.java:144)
	at javax.xml.parsers.FactoryFinder.findJarServiceProvider(FactoryFinder.java:296)
	at javax.xml.parsers.FactoryFinder.find(FactoryFinder.java:221)
	at javax.xml.parsers.DocumentBuilderFactory.newInstance(DocumentBuilderFactory.java:120)
	at java.util.prefs.XmlSupport.loadPrefsDoc(XmlSupport.java:241)
	at java.util.prefs.XmlSupport.importMap(XmlSupport.java:375)
	at java.util.prefs.FileSystemPreferences$7.run(FileSystemPreferences.java:578)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.util.prefs.FileSystemPreferences.loadCache(FileSystemPreferences.java:571)
	at java.util.prefs.FileSystemPreferences.initCacheIfNecessary(FileSystemPreferences.java:554)
	at java.util.prefs.FileSystemPreferences.getSpi(FileSystemPreferences.java:531)
	at java.util.prefs.AbstractPreferences.get(AbstractPreferences.java:287)
	at com.aurigma.imageuploader.tools.j.h(Unknown Source)
	at com.aurigma.imageuploader.bq.L(Unknown Source)
	at com.aurigma.imageuploader.ImageUploader.init(Unknown Source)
	at sun.applet.AppletPanel.run(AppletPanel.java:436)
	at java.lang.Thread.run(Thread.java:636)
mano@mano-laptop:~$ 

```

Any suggestion, please?
Thanks

Ubuntu Lucid
Acer Aspire 5730Z
Linux mano-laptop 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 x86_64 GNU/Linux
Firefox 3.6.3

---

### Post by manolomanolo on 2010-06-25
Up

---

### Post by Sub101 on 2010-06-25
I would expect this would still work.

[http://ubuntuforums.org/showthread.php?t=595398](http://ubuntuforums.org/showthread.php?t=595398)

---

### Post by manolomanolo on 2010-06-25
Hi Sub101

Thanks for your reply.

Which part of that discussion can solve my problem? Is it enough to follow the instructions of the second post?

thanks.

---

### Post by manolomanolo on 2010-06-25
```
sudo apt-get remove gcj libgcj-common libgcj7-0
[sudo] password for mano: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package gcj is not installed, so not removed
Package libgcj-common is not installed, so not removed
E: Couldn't find package libgcj7-0

```

---

