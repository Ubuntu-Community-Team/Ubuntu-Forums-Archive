---
title: "Eclipse Not Starting"
date: 2005-11-19
forum: Desktop Environments
---

### Post by imnes on 2005-11-19
Have Eclipse installed on Breezy, it's not starting. 

```
nicholas@thinkpad:~$ echo $PATH
/usr/local/bin:/usr/local/sbin:/sbin:/usr/sbin:/bin:/usr/bin:/usr/bin/X11:/usr/games
nicholas@thinkpad:~$ eclipse
searching for compatible vm...
  testing /usr/lib/jvm/java-gcj...found

```

At this point I get a error dialog that says:

```
An error has occurred. See the log file
/home/nicholas/.eclipse/org.eclipse.platform_3.1.1/configuration/1132457824085.log.
```

That file contains:

```
!SESSION 2005-11-19 22:37:03.846 -----------------------------------------------
eclipse.buildId=
java.fullversion=GNU libgcj 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_US
Framework arguments:  
Command-line arguments:  -os linux -ws gtk -arch x86 

!ENTRY initial@reference:file:plugins/org.eclipse.core.runtime_3.1.1.jar/ 0 0 2005-11-19 22:37:05.28
!MESSAGE FrameworkEvent.ERROR
!STACK 0
org.osgi.framework.BundleException: Exception in org.eclipse.core.internal.runtime.PlatformActivator.start() of bundle org.eclipse.core.runtime.
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(org.osgi.framework.BundleActivator) (/usr/lib/eclipse/plugins.gcj/org.eclipse.osgi_3.1.1.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start() (/usr/lib/eclipse/plugins.gcj/org.eclipse.osgi_3.1.1.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(boolean) (/usr/lib/eclipse/plugins.gcj/org.eclipse.osgi_3.1.1.jar.so)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.resume() (/usr/lib/eclipse/plugins.gcj/org.eclipse.osgi_3.1.1.jar.so)
   at org.eclipse.osgi.framework.internal.core.Framework.resumeBundle(org.eclipse.osgi.framework.internal.core.AbstractBundle) (/usr/lib/eclipse/plugins.gcj/org.eclipse.osgi_3.1.1.jar.so)
   at org.eclipse.osgi.framework.internal.core.StartLevelManager.resumeBundles(org.eclipse.osgi.framework.internal.core.AbstractBundle[], boolean) (/usr/lib/eclipse/plugins.gcj/org.eclipse.osgi_3.1.1.jar.so)
   at org.eclipse.osgi.framework.internal.core.StartLevelManager.incFWSL(int, org.eclipse.osgi.framework.internal.core.AbstractBundle) (/usr/lib/eclipse/plugins.gcj/org.eclipse.osgi_3.1.1.jar.so)
   at org.eclipse.osgi.framework.internal.core.StartLevelManager.doSetStartLevel(int, org.eclipse.osgi.framework.internal.core.AbstractBundle) (/usr/lib/eclipse/plugins.gcj/org.eclipse.osgi_3.1.1.jar.so)
   at org.eclipse.osgi.framework.internal.core.StartLevelManager.dispatchEvent(java.lang.Object, java.lang.Object, int, java.lang.Object) (/usr/lib/eclipse/plugins.gcj/org.eclipse.osgi_3.1.1.jar.so)
   at org.eclipse.osgi.framework.eventmgr.EventManager.dispatchEvent(org.eclipse.osgi.framework.eventmgr.EventListeners$ListElement[], org.eclipse.osgi.framework.eventmgr.EventDispatcher, int, java.lang.Object) (/usr/lib/eclipse/plugins.gcj/org.eclipse.osgi_3.1.1.jar.so)
   at org.eclipse.osgi.framework.eventmgr.EventManager$EventThread.run() (/usr/lib/eclipse/plugins.gcj/org.eclipse.osgi_3.1.1.jar.so)
   at .GC_start_routine (/usr/lib/libgcj.so.6.0.0)
   at .__clone (/lib/tls/i686/cmov/libc-2.3.5.so)
Caused by: java.lang.NullPointerException
   at org.eclipse.core.internal.runtime.InternalPlatform.getSplashHandler() (/usr/lib/eclipse/plugins.gcj/org.eclipse.core.runtime_3.1.1.jar.so)
   at org.eclipse.core.internal.runtime.InternalPlatform.start(org.osgi.framework.BundleContext) (/usr/lib/eclipse/plugins.gcj/org.eclipse.core.runtime_3.1.1.jar.so)
   at org.eclipse.core.internal.runtime.PlatformActivator.startInternalPlatform() (/usr/lib/eclipse/plugins.gcj/org.eclipse.core.runtime_3.1.1.jar.so)
   at org.eclipse.core.internal.runtime.PlatformActivator.start(org.osgi.framework.BundleContext) (/usr/lib/eclipse/plugins.gcj/org.eclipse.core.runtime_3.1.1.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl$2.run() (/usr/lib/eclipse/plugins.gcj/org.eclipse.osgi_3.1.1.jar.so)
   at java.security.AccessController.doPrivileged(java.security.PrivilegedExceptionAction) (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(org.osgi.framework.BundleActivator) (/usr/lib/eclipse/plugins.gcj/org.eclipse.osgi_3.1.1.jar.so)
   ...12 more
Root exception:
java.lang.NullPointerException
   at org.eclipse.core.internal.runtime.InternalPlatform.getSplashHandler() (/usr/lib/eclipse/plugins.gcj/org.eclipse.core.runtime_3.1.1.jar.so)
   at org.eclipse.core.internal.runtime.InternalPlatform.start(org.osgi.framework.BundleContext) (/usr/lib/eclipse/plugins.gcj/org.eclipse.core.runtime_3.1.1.jar.so)
   at org.eclipse.core.internal.runtime.PlatformActivator.startInternalPlatform() (/usr/lib/eclipse/plugins.gcj/org.eclipse.core.runtime_3.1.1.jar.so)
   at org.eclipse.core.internal.runtime.PlatformActivator.start(org.osgi.framework.BundleContext) (/usr/lib/eclipse/plugins.gcj/org.eclipse.core.runtime_3.1.1.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl$2.run() (/usr/lib/eclipse/plugins.gcj/org.eclipse.osgi_3.1.1.jar.so)
   at java.security.AccessController.doPrivileged(java.security.PrivilegedExceptionAction) (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(org.osgi.framework.BundleActivator) (/usr/lib/eclipse/plugins.gcj/org.eclipse.osgi_3.1.1.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start() (/usr/lib/eclipse/plugins.gcj/org.eclipse.osgi_3.1.1.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(boolean) (/usr/lib/eclipse/plugins.gcj/org.eclipse.osgi_3.1.1.jar.so)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.resume() (/usr/lib/eclipse/plugins.gcj/org.eclipse.osgi_3.1.1.jar.so)
   at org.eclipse.osgi.framework.internal.core.Framework.resumeBundle(org.eclipse.osgi.framework.internal.core.AbstractBundle) (/usr/lib/eclipse/plugins.gcj/org.eclipse.osgi_3.1.1.jar.so)
   at org.eclipse.osgi.framework.internal.core.StartLevelManager.resumeBundles(org.eclipse.osgi.framework.internal.core.AbstractBundle[], boolean) (/usr/lib/eclipse/plugins.gcj/org.eclipse.osgi_3.1.1.jar.so)
   at org.eclipse.osgi.framework.internal.core.StartLevelManager.incFWSL(int, org.eclipse.osgi.framework.internal.core.AbstractBundle) (/usr/lib/eclipse/plugins.gcj/org.eclipse.osgi_3.1.1.jar.so)
   at org.eclipse.osgi.framework.internal.core.StartLevelManager.doSetStartLevel(int, org.eclipse.osgi.framework.internal.core.AbstractBundle) (/usr/lib/eclipse/plugins.gcj/org.eclipse.osgi_3.1.1.jar.so)
   at org.eclipse.osgi.framework.internal.core.StartLevelManager.dispatchEvent(java.lang.Object, java.lang.Object, int, java.lang.Object) (/usr/lib/eclipse/plugins.gcj/org.eclipse.osgi_3.1.1.jar.so)
   at org.eclipse.osgi.framework.eventmgr.EventManager.dispatchEvent(org.eclipse.osgi.framework.eventmgr.EventListeners$ListElement[], org.eclipse.osgi.framework.eventmgr.EventDispatcher, int, java.lang.Object) (/usr/lib/eclipse/plugins.gcj/org.eclipse.osgi_3.1.1.jar.so)
   at org.eclipse.osgi.framework.eventmgr.EventManager$EventThread.run() (/usr/lib/eclipse/plugins.gcj/org.eclipse.osgi_3.1.1.jar.so)
   at .GC_start_routine (/usr/lib/libgcj.so.6.0.0)
   at .__clone (/lib/tls/i686/cmov/libc-2.3.5.so)

!ENTRY initial@reference:file:plugins/org.eclipse.update.configurator_3.1.0.jar/ 0 0 2005-11-19 22:37:05.129
!MESSAGE FrameworkEvent.ERROR
!STACK 0
org.osgi.framework.BundleException: Exception in org.eclipse.update.internal.configurator.ConfigurationActivator.start() of bundle org.eclipse.update.configurator.
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(org.osgi.framework.BundleActivator) (/usr/lib/eclipse/plugins.gcj/org.eclipse.osgi_3.1.1.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start() (/usr/lib/eclipse/plugins.gcj/org.eclipse.osgi_3.1.1.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(boolean) (/usr/lib/eclipse/plugins.gcj/org.eclipse.osgi_3.1.1.jar.so)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.resume() (/usr/lib/eclipse/plugins.gcj/org.eclipse.osgi_3.1.1.jar.so)
   at org.eclipse.osgi.framework.internal.core.Framework.resumeBundle(org.eclipse.osgi.framework.internal.core.AbstractBundle) (/usr/lib/eclipse/plugins.gcj/org.eclipse.osgi_3.1.1.jar.so)
   at org.eclipse.osgi.framework.internal.core.StartLevelManager.resumeBundles(org.eclipse.osgi.framework.internal.core.AbstractBundle[], boolean) (/usr/lib/eclipse/plugins.gcj/org.eclipse.osgi_3.1.1.jar.so)
   at org.eclipse.osgi.framework.internal.core.StartLevelManager.incFWSL(int, org.eclipse.osgi.framework.internal.core.AbstractBundle) (/usr/lib/eclipse/plugins.gcj/org.eclipse.osgi_3.1.1.jar.so)
   at org.eclipse.osgi.framework.internal.core.StartLevelManager.doSetStartLevel(int, org.eclipse.osgi.framework.internal.core.AbstractBundle) (/usr/lib/eclipse/plugins.gcj/org.eclipse.osgi_3.1.1.jar.so)
   at org.eclipse.osgi.framework.internal.core.StartLevelManager.dispatchEvent(java.lang.Object, java.lang.Object, int, java.lang.Object) (/usr/lib/eclipse/plugins.gcj/org.eclipse.osgi_3.1.1.jar.so)
   at org.eclipse.osgi.framework.eventmgr.EventManager.dispatchEvent(org.eclipse.osgi.framework.eventmgr.EventListeners$ListElement[], org.eclipse.osgi.framework.eventmgr.EventDispatcher, int, java.lang.Object) (/usr/lib/eclipse/plugins.gcj/org.eclipse.osgi_3.1.1.jar.so)
   at org.eclipse.osgi.framework.eventmgr.EventManager$EventThread.run() (/usr/lib/eclipse/plugins.gcj/org.eclipse.osgi_3.1.1.jar.so)
   at .GC_start_routine (/usr/lib/libgcj.so.6.0.0)
   at .__clone (/lib/tls/i686/cmov/libc-2.3.5.so)
Caused by: java.lang.Exception: Cannot initialize the Update Configurator
   at org.eclipse.update.internal.configurator.ConfigurationActivator.initialize() (/usr/lib/eclipse/plugins.gcj/org.eclipse.update.configurator_3.1.0.jar.so)
   at org.eclipse.update.internal.configurator.ConfigurationActivator.start(org.osgi.framework.BundleContext) (/usr/lib/eclipse/plugins.gcj/org.eclipse.update.configurator_3.1.0.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl$2.run() (/usr/lib/eclipse/plugins.gcj/org.eclipse.osgi_3.1.1.jar.so)
   at java.security.AccessController.doPrivileged(java.security.PrivilegedExceptionAction) (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(org.osgi.framework.BundleActivator) (/usr/lib/eclipse/plugins.gcj/org.eclipse.osgi_3.1.1.jar.so)
   ...12 more
Root exception:
java.lang.Exception: Cannot initialize the Update Configurator
   at org.eclipse.update.internal.configurator.ConfigurationActivator.initialize() (/usr/lib/eclipse/plugins.gcj/org.eclipse.update.configurator_3.1.0.jar.so)
   at org.eclipse.update.internal.configurator.ConfigurationActivator.start(org.osgi.framework.BundleContext) (/usr/lib/eclipse/plugins.gcj/org.eclipse.update.configurator_3.1.0.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl$2.run() (/usr/lib/eclipse/plugins.gcj/org.eclipse.osgi_3.1.1.jar.so)
   at java.security.AccessController.doPrivileged(java.security.PrivilegedExceptionAction) (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(org.osgi.framework.BundleActivator) (/usr/lib/eclipse/plugins.gcj/org.eclipse.osgi_3.1.1.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start() (/usr/lib/eclipse/plugins.gcj/org.eclipse.osgi_3.1.1.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(boolean) (/usr/lib/eclipse/plugins.gcj/org.eclipse.osgi_3.1.1.jar.so)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.resume() (/usr/lib/eclipse/plugins.gcj/org.eclipse.osgi_3.1.1.jar.so)
   at org.eclipse.osgi.framework.internal.core.Framework.resumeBundle(org.eclipse.osgi.framework.internal.core.AbstractBundle) (/usr/lib/eclipse/plugins.gcj/org.eclipse.osgi_3.1.1.jar.so)
   at org.eclipse.osgi.framework.internal.core.StartLevelManager.resumeBundles(org.eclipse.osgi.framework.internal.core.AbstractBundle[], boolean) (/usr/lib/eclipse/plugins.gcj/org.eclipse.osgi_3.1.1.jar.so)
   at org.eclipse.osgi.framework.internal.core.StartLevelManager.incFWSL(int, org.eclipse.osgi.framework.internal.core.AbstractBundle) (/usr/lib/eclipse/plugins.gcj/org.eclipse.osgi_3.1.1.jar.so)
   at org.eclipse.osgi.framework.internal.core.StartLevelManager.doSetStartLevel(int, org.eclipse.osgi.framework.internal.core.AbstractBundle) (/usr/lib/eclipse/plugins.gcj/org.eclipse.osgi_3.1.1.jar.so)
   at org.eclipse.osgi.framework.internal.core.StartLevelManager.dispatchEvent(java.lang.Object, java.lang.Object, int, java.lang.Object) (/usr/lib/eclipse/plugins.gcj/org.eclipse.osgi_3.1.1.jar.so)
   at org.eclipse.osgi.framework.eventmgr.EventManager.dispatchEvent(org.eclipse.osgi.framework.eventmgr.EventListeners$ListElement[], org.eclipse.osgi.framework.eventmgr.EventDispatcher, int, java.lang.Object) (/usr/lib/eclipse/plugins.gcj/org.eclipse.osgi_3.1.1.jar.so)
   at org.eclipse.osgi.framework.eventmgr.EventManager$EventThread.run() (/usr/lib/eclipse/plugins.gcj/org.eclipse.osgi_3.1.1.jar.so)
   at .GC_start_routine (/usr/lib/libgcj.so.6.0.0)
   at .__clone (/lib/tls/i686/cmov/libc-2.3.5.so)

!ENTRY org.eclipse.osgi 2005-11-19 22:37:05.161
!MESSAGE Startup error
!STACK 1
java.lang.IllegalStateException: Bundle initial@reference:file:plugins/org.eclipse.core.runtime_3.1.1.jar/ [1] is not active.
   at org.eclipse.core.runtime.adaptor.EclipseStarter.ensureBundlesActive(org.osgi.framework.Bundle[]) (/usr/lib/eclipse/plugins.gcj/org.eclipse.osgi_3.1.1.jar.so)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.startup(java.lang.String[], java.lang.Runnable) (/usr/lib/eclipse/plugins.gcj/org.eclipse.osgi_3.1.1.jar.so)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(java.lang.String[], java.lang.Runnable) (/usr/lib/eclipse/plugins.gcj/org.eclipse.osgi_3.1.1.jar.so)
   at java.lang.reflect.Method.invoke(java.lang.Object, java.lang.Object[]) (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.core.launcher.Main.invokeFramework(java.lang.String[], java.net.URL[]) (/usr/lib/eclipse/plugins.gcj/org.eclipse.platform_3.1.1/startup.jar.so)
   at org.eclipse.core.launcher.Main.basicRun(java.lang.String[]) (/usr/lib/eclipse/plugins.gcj/org.eclipse.platform_3.1.1/startup.jar.so)
   at org.eclipse.core.launcher.Main.run(java.lang.String[]) (/usr/lib/eclipse/plugins.gcj/org.eclipse.platform_3.1.1/startup.jar.so)
   at org.eclipse.core.launcher.Main.main(java.lang.String[]) (/usr/lib/eclipse/plugins.gcj/org.eclipse.platform_3.1.1/startup.jar.so)
   at gnu.java.lang.MainThread.call_main() (/usr/lib/libgcj.so.6.0.0)
   at gnu.java.lang.MainThread.run() (/usr/lib/libgcj.so.6.0.0)

```


Tried deleting ~/.eclipse and ~/workspace and restarting the IDE but still no luck.  Anybody know what I've done wrong?

And just incase I have some conflicting packages installed somehow, here's a list of everything I could find installed relating to eclipse.  (May be duplicates listed)

```

libswt3.1-gtk-java/unknown uptodate 3.1.1-1ubuntu3
libswt3.1-gtk-jni/unknown uptodate 3.1.1-1ubuntu3
eclipse-platform/unknown uptodate 3.1.1-1ubuntu3
eclipse-jdt/unknown uptodate 3.1.1-1ubuntu3
eclipse-source/unknown uptodate 3.1.1-1ubuntu3
eclipse-jdt-common/unknown uptodate 3.1.1-1ubuntu3
eclipse-ecj-gcj/unknown uptodate 3.1.1-1ubuntu3
eclipse-platform-gcj/unknown uptodate 3.1.1-1ubuntu3
eclipse-efj/unknown uptodate 3.1.1-1ubuntu3
eclipse-sdk/unknown uptodate 3.1.1-1ubuntu3
eclipse-rcp-common/unknown uptodate 3.1.1-1ubuntu3
eclipse-rcp/unknown uptodate 3.1.1-1ubuntu3
eclipse-pde/unknown uptodate 3.1.1-1ubuntu3
eclipse-pde-gcj/unknown uptodate 3.1.1-1ubuntu3
eclipse-rcp-gcj/unknown uptodate 3.1.1-1ubuntu3
eclipse-pde-common/unknown uptodate 3.1.1-1ubuntu3
eclipse-jdt-gcj/unknown uptodate 3.1.1-1ubuntu3
eclipse-platform-common/unknown uptodate 3.1.1-1ubuntu3
eclipse-base/unknown uptodate 3.1.1-1ubuntu3
eclipse-ecj/unknown uptodate 3.1.1-1ubuntu3
libgcj-common/unknown uptodate 1:4.0.1-4ubuntu9
libgcj6-common/unknown uptodate 4.0.1-4ubuntu9
java-gcj-compat/unknown uptodate 1.0.30-4
eclipse-pde-gcj/unknown uptodate 3.1.1-1ubuntu3
eclipse-rcp-gcj/unknown uptodate 3.1.1-1ubuntu3
libgcj6/unknown uptodate 4.0.1-4ubuntu9
eclipse-jdt-gcj/unknown uptodate 3.1.1-1ubuntu3
libgcj6-awt/unknown uptodate 4.0.1-4ubuntu9

```

---

### Post by cstudent on 2005-11-20
Eclipse won't run using the default Gnu Java libraries. I would suggest installing the Sun Java version. You can easily install it using Automatix.

[http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)

Bill

---

