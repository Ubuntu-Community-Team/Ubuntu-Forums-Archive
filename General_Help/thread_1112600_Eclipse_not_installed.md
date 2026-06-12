---
title: "Eclipse not installed?"
date: 2009-03-31
forum: General Help
---

### Post by johannes_h on 2009-03-31
Hi.
I have downloaded two eclipse softwares.. One for java, and one for php. I don't want to mix them..

The java version works, not the php if I try to run from terminal. I would like a shortcut on the panel, but it only works for the java version.

I downloaded both eclipses "my self", not with any apt-get ...

This is what I get in the terminal:

> The program 'eclipse' is currently not installed.  You can install it by typing:
sudo apt-get install eclipse
bash: eclipse: command not found

The one I get from apt-get is not the one I'm looking for.. I want this one to open in terminal (through), so I can make a shortcut..

---

### Post by cariboo on 2009-03-31
Because you installed eclipse manually you have to enter the full path to the executeable in the terminal to run it eg:

```
/opt/eclipse/eclipse
```

The above command is only an example. To create a Launcher. right-click on the desktop and select Create Launcher. Fill in the details and drag the launcher to the panel. Almost just like creating a Windows shortcut. :)

Jim

---

### Post by johannes_h on 2009-04-01
> **cariboo907 said:**
> Because you installed eclipse manually you have to enter the full path to the executeable in the terminal to run it eg:

```
/opt/eclipse/eclipse
```

The above command is only an example. To create a Launcher. right-click on the desktop and select Create Launcher. Fill in the details and drag the launcher to the panel. Almost just like creating a Windows shortcut. :)

Jim

Thanks to you very many! :D

---

### Post by pcjunkie on 2009-04-02
I am getting all sorts of errors..

> !ENTRY org.eclipse.osgi 4 0 2009-04-02 20:31:20.132
!MESSAGE Error reading configuration: /opt/eclipse/configuration/org.eclipse.osgi/.manager/.fileTableLock (No such file or directory)
!STACK 0
java.io.FileNotFoundException: /opt/eclipse/configuration/org.eclipse.osgi/.manager/.fileTableLock (No such file or directory)
	at java.io.RandomAccessFile.open(Native Method)
	at java.io.RandomAccessFile.<init>(RandomAccessFile.java:233)
	at org.eclipse.core.runtime.internal.adaptor.Locker_JavaNio.lock(Locker_JavaNio.java:32)
	at org.eclipse.osgi.storagemanager.StorageManager.lock(StorageManager.java:389)
	at org.eclipse.osgi.storagemanager.StorageManager.open(StorageManager.java:687)
	at org.eclipse.osgi.internal.baseadaptor.BaseStorage.initFileManager(BaseStorage.java:208)
	at org.eclipse.osgi.internal.baseadaptor.BaseStorage.initialize(BaseStorage.java:142)
	at org.eclipse.osgi.baseadaptor.BaseAdaptor.initializeStorage(BaseAdaptor.java:124)
	at org.eclipse.osgi.framework.internal.core.Framework.initialize(Framework.java:180)
	at org.eclipse.osgi.framework.internal.core.Framework.<init>(Framework.java:152)
	at org.eclipse.osgi.framework.internal.core.OSGi.createFramework(OSGi.java:90)
	at org.eclipse.osgi.framework.internal.core.OSGi.<init>(OSGi.java:31)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.startup(EclipseStarter.java:286)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:175)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:549)
	at org.eclipse.equinox.launcher.Main.basicRun(Main.java:504)
	at org.eclipse.equinox.launcher.Main.run(Main.java:1236)




---

