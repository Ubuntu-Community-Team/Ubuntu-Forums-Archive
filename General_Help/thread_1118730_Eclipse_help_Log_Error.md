---
title: "Eclipse help Log Error"
date: 2009-04-07
forum: General Help
---

### Post by Ginny on 2009-04-07
i have installed eclipse3.0 Whenever i start i get this msg "Error has occured. see the log file configration\12534XXX"
the log file shoe this following:

!SESSION Apr 07, 2009 19:19:31.890 ---------------------------------------------
eclipse.buildId=M200409161125
java.version=1.7.0-ea
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=win32, ARCH=x86, WS=win32, NL=en_US

!ENTRY initial@reference:file:c:/Program Files/eclipse3.0/plugins/org.eclipse.core.runtime_3.0.1/ 0 0 Apr 07, 2009 19:19:31.890
!MESSAGE FrameworkEvent.ERROR
!STACK 0
org.osgi.framework.BundleException: Exception in org.eclipse.core.internal.runtime.PlatformActivator.start() of bundle org.eclipse.core.runtime.
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:975)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:937)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:421)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.resume(AbstractBundle.java:366)
	at org.eclipse.osgi.framework.internal.core.Framework.resumeBundle(Framework.java:999)
	at org.eclipse.osgi.framework.internal.core.StartLevelManager.resumeBundles(StartLevelManager.java:577)
	at org.eclipse.osgi.framework.internal.core.StartLevelManager.incFWSL(StartLevelManager.java:488)
	at org.eclipse.osgi.framework.internal.core.StartLevelManager.doSetStartLevel(StartLevelManager.java:273)
	at org.eclipse.osgi.framework.internal.core.StartLevelManager.dispatchEvent(StartLevelManager.java:444)
	at org.eclipse.osgi.framework.eventmgr.EventManager.dispatchEvent(EventManager.java:186)
	at org.eclipse.osgi.framework.eventmgr.EventThread.run(EventThread.java:104)
Caused by: java.io.IOException: An error occurred while locking file "c:\Program Files\eclipse3.0\configuration\org.eclipse.core.runtime\.manager\.fileTableLock": "Access is denied". A probably reason is that the file system or Runtime Environment does not support file locking. You may want to choose a different location, or disable file locking (using the osgi.locking property), but this can cause data corruption.
	at org.eclipse.core.runtime.adaptor.Locker_JavaNio.lock(Locker_JavaNio.java:42)
	at org.eclipse.osgi.service.datalocation.FileManager.lock(FileManager.java:219)
	at org.eclipse.osgi.service.datalocation.FileManager.open(FileManager.java:423)
	at org.eclipse.core.internal.runtime.InternalPlatform.initializeRuntimeFileManager(InternalPlatform.java:391)
	at org.eclipse.core.internal.runtime.InternalPlatform.start(InternalPlatform.java:384)
	at org.eclipse.core.internal.runtime.PlatformActivator.startInternalPlatform(PlatformActivator.java:251)
	at org.eclipse.core.internal.runtime.PlatformActivator.start(PlatformActivator.java:64)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl$1.run(BundleContextImpl.java:958)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:954)
	... 10 more
Root exception:
java.io.IOException: An error occurred while locking file "c:\Program Files\eclipse3.0\configuration\org.eclipse.core.runtime\.manager\.fileTableLock": "Access is denied". A probably reason is that the file system or Runtime Environment does not support file locking. You may want to choose a different location, or disable file locking (using the osgi.locking property), but this can cause data corruption.
	at org.eclipse.core.runtime.adaptor.Locker_JavaNio.lock(Locker_JavaNio.java:42)
	at org.eclipse.osgi.service.datalocation.FileManager.lock(FileManager.java:219)
	at org.eclipse.osgi.service.datalocation.FileManager.open(FileManager.java:423)
	at org.eclipse.core.internal.runtime.InternalPlatform.initializeRuntimeFileManager(InternalPlatform.java:391)
	at org.eclipse.core.internal.runtime.InternalPlatform.start(InternalPlatform.java:384)
	at org.eclipse.core.internal.runtime.PlatformActivator.startInternalPlatform(PlatformActivator.java:251)
	at org.eclipse.core.internal.runtime.PlatformActivator.start(PlatformActivator.java:64)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl$1.run(BundleContextImpl.java:958)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:954)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:937)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:421)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.resume(AbstractBundle.java:366)
	at org.eclipse.osgi.framework.internal.core.Framework.resumeBundle(Framework.java:999)
	at org.eclipse.osgi.framework.internal.core.StartLevelManager.resumeBundles(StartLevelManager.java:577)
	at org.eclipse.osgi.framework.internal.core.StartLevelManager.incFWSL(StartLevelManager.java:488)
	at org.eclipse.osgi.framework.internal.core.StartLevelManager.doSetStartLevel(StartLevelManager.java:273)
	at org.eclipse.osgi.framework.internal.core.StartLevelManager.dispatchEvent(StartLevelManager.java:444)
	at org.eclipse.osgi.framework.eventmgr.EventManager.dispatchEvent(EventManager.java:186)
	at org.eclipse.osgi.framework.eventmgr.EventThread.run(EventThread.java:104)

!ENTRY initial@reference:file:c:/Program Files/eclipse3.0/plugins/org.eclipse.update.configurator_3.0.0/ 0 0 Apr 07, 2009 19:19:31.921
!MESSAGE FrameworkEvent.ERROR
!STACK 0
org.osgi.framework.BundleException: Exception in org.eclipse.update.internal.configurator.ConfigurationActivator.start() of bundle org.eclipse.update.configurator.
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:975)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:937)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:421)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.resume(AbstractBundle.java:366)
	at org.eclipse.osgi.framework.internal.core.Framework.resumeBundle(Framework.java:999)
	at org.eclipse.osgi.framework.internal.core.StartLevelManager.resumeBundles(StartLevelManager.java:577)
	at org.eclipse.osgi.framework.internal.core.StartLevelManager.incFWSL(StartLevelManager.java:488)
	at org.eclipse.osgi.framework.internal.core.StartLevelManager.doSetStartLevel(StartLevelManager.java:273)
	at org.eclipse.osgi.framework.internal.core.StartLevelManager.dispatchEvent(StartLevelManager.java:444)
	at org.eclipse.osgi.framework.eventmgr.EventManager.dispatchEvent(EventManager.java:186)
	at org.eclipse.osgi.framework.eventmgr.EventThread.run(EventThread.java:104)
Caused by: java.lang.Exception: Cannot initialize the Update Configurator
	at org.eclipse.update.internal.configurator.ConfigurationActivator.initialize(ConfigurationActivator.java:93)
	at org.eclipse.update.internal.configurator.ConfigurationActivator.start(ConfigurationActivator.java:71)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl$1.run(BundleContextImpl.java:958)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:954)
	... 10 more
Root exception:
java.lang.Exception: Cannot initialize the Update Configurator
	at org.eclipse.update.internal.configurator.ConfigurationActivator.initialize(ConfigurationActivator.java:93)
	at org.eclipse.update.internal.configurator.ConfigurationActivator.start(ConfigurationActivator.java:71)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl$1.run(BundleContextImpl.java:958)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:954)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:937)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:421)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.resume(AbstractBundle.java:366)
	at org.eclipse.osgi.framework.internal.core.Framework.resumeBundle(Framework.java:999)
	at org.eclipse.osgi.framework.internal.core.StartLevelManager.resumeBundles(StartLevelManager.java:577)
	at org.eclipse.osgi.framework.internal.core.StartLevelManager.incFWSL(StartLevelManager.java:488)
	at org.eclipse.osgi.framework.internal.core.StartLevelManager.doSetStartLevel(StartLevelManager.java:273)
	at org.eclipse.osgi.framework.internal.core.StartLevelManager.dispatchEvent(StartLevelManager.java:444)
	at org.eclipse.osgi.framework.eventmgr.EventManager.dispatchEvent(EventManager.java:186)
	at org.eclipse.osgi.framework.eventmgr.EventThread.run(EventThread.java:104)

!ENTRY org.eclipse.osgi Apr 07, 2009 19:19:31.921
!MESSAGE Startup error
!STACK 1
java.lang.IllegalStateException: Bundle initial@reference:file:c:/Program Files/eclipse3.0/plugins/org.eclipse.core.runtime_3.0.1/ [1] is not active.
	at org.eclipse.core.runtime.adaptor.EclipseStarter.ensureBundlesActive(EclipseStarter.java:303)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.startup(EclipseStarter.java:227)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:127)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
	at java.lang.reflect.Method.invoke(Unknown Source)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:185)
	at org.eclipse.core.launcher.Main.run(Main.java:704)
	at org.eclipse.core.launcher.Main.main(Main.java:688)


Please help me .....

---

