---
title: "RadRails on Dapper"
date: 2006-10-03
forum: Desktop Environments
---

### Post by Hpatoio on 2006-10-03
Hello, I've follwed these instructions to install RadRails
[www.radrails.org/blog/2006/9/18/installing-radrails-on-ubuntu-dapper]("www.radrails.org/blog/2006/9/18/installing-radrails-on-ubuntu-dapper")

The point is that the application is not working.

When I run it I get a popUp that tells me to look on the log file because error has happend.

The error is :

[INDENT]
!SESSION 2006-10-03 22:30:38.005 -----------------------------------------------
eclipse.buildId=unknown
java.version=1.5.0_06
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_AU
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.osgi 4 0 2006-10-03 22:30:42.272
!MESSAGE Application error
!STACK 1
java.lang.UnsatisfiedLinkError: /home/simone/.eclipse/org.radrails.ide.ui.application_0.7.1/configuration/org.eclipse.osgi/bundles/59/1/.cp/libswt-pi-gtk-3232.so: /home/simone/.eclipse/org.radrails.ide.ui.application_0.7.1/configuration/org.eclipse.osgi/bundles/59/1/.cp/libswt-pi-gtk-3232.so: cannot open shared object file: No such file or directory
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1751)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1660)
	at java.lang.Runtime.loadLibrary0(Runtime.java:822)
	at java.lang.System.loadLibrary(System.java:992)
	at org.eclipse.swt.internal.Library.loadLibrary(Library.java:123)
	at org.eclipse.swt.internal.gtk.OS.<clinit>(OS.java:22)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
	at org.eclipse.swt.widgets.Display.<clinit>(Display.java:126)
	at org.eclipse.ui.internal.Workbench.createDisplay(Workbench.java:433)
	at org.eclipse.ui.PlatformUI.createDisplay(PlatformUI.java:161)
	at org.radrails.ide.ui.RadRails.createDisplay(RadRails.java:104)
	at org.radrails.ide.ui.RadRails.run(RadRails.java:59)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:78)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:92)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:68)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:585)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)

!ENTRY org.eclipse.osgi 2 0 2006-10-03 22:30:42.348
!MESSAGE One or more bundles are not resolved because the following root constraints are not resolved:
!SUBENTRY 1 org.eclipse.osgi 2 0 2006-10-03 22:30:42.349
!MESSAGE Bundle [email]update@plugins/org.eclipse.plat[/email]form_3.2.0.v20060601/ was not resolved.
!SUBENTRY 2 org.eclipse.platform 2 0 2006-10-03 22:30:42.349
!MESSAGE Missing required bundle org.eclipse.ui.intro.universal_[3.2.0,4.0.0).

!ENTRY org.eclipse.osgi 2 0 2006-10-03 22:30:42.361
!MESSAGE The following is a complete list of bundles which are not resolved, see the prior log entry for the root cause if it exists:
!SUBENTRY 1 org.eclipse.osgi 2 0 2006-10-03 22:30:42.381
!MESSAGE Bundle [email]update@plugins/org.eclipse.plat[/email]form_3.2.0.v20060601/ [8] was not resolved.
!SUBENTRY 2 org.eclipse.platform 2 0 2006-10-03 22:30:42.381
!MESSAGE Missing required bundle org.eclipse.ui.intro.universal_[3.2.0,4.0.0).
[/INDENT]

I'm on Ubuntu Dapper with and AMD 64.

Ideas ?

Simone

---

