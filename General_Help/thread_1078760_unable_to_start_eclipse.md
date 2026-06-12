---
title: "unable to start eclipse"
date: 2009-02-23
forum: General Help
---

### Post by mhdazeem on 2009-02-23
Hi guyz, I am newbie to linux & eclipse. My system was working perfectly with eclipse and suddenly my system turned off. When I restarted the system it shows an error " check logs from workspace/.metadata/.logs". Now the problem is I am unable to open the eclipse... Please have a look on log file,...Please help me out... thanks in advance...
 
 !SESSION 2009-02-20 15:32:24.886 -----------------------------------------------
 eclipse.buildId=M20070212-1330
 java.fullversion=GNU libgcj 4.2.4 (Ubuntu 4.2.4-1ubuntu3)
 BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_AU
 Command-line arguments: -os linux -ws gtk -arch x86
 
 This is a continuation of log file /home/clive/workspace/.metadata/.bak_0.log
 Created Time: 2009-02-20 15:32:49.630
 
 !ENTRY org.eclipse.osgi 4 0 2009-02-20 15:32:49.630
 !MESSAGE Application error
 !STACK 1
 java.lang.NoClassDefFoundError: org.eclipse.ui.internal.ide.IDEWorkbenchAdvisor
 at java.lang.Class.initializeClass(libgcj.so.81)
 at org.eclipse.ui.internal.ide.IDEApplication.run(org .eclipse.ui.ide_3.2.1.M20060915-1030.jar.so)
 at org.eclipse.core.internal.runtime.PlatformActivato r$1.run(org.eclipse.core.runtime_3.2.0.v20060603.j ar.so)
 at org.eclipse.core.runtime.internal.adaptor.EclipseA ppLauncher.runApplication(org.eclipse.osgi_3.2.2.R 32x_v20070118.jar.so)
 at org.eclipse.core.runtime.internal.adaptor.EclipseA ppLauncher.start(org.eclipse.osgi_3.2.2.R32x_v2007 0118.jar.so)
 at org.eclipse.core.runtime.adaptor.EclipseStarter.ru n(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
 at org.eclipse.core.runtime.adaptor.EclipseStarter.ru n(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
 at java.lang.reflect.Method.invoke(libgcj.so.81)
 at org.eclipse.core.launcher.Main.invokeFramework(Mai n.java:336)
 at org.eclipse.core.launcher.Main.basicRun(Main.java: 280)
 at org.eclipse.core.launcher.Main.run(Main.java:977)
 at org.eclipse.core.launcher.Main.main(Main.java:952)
 Caused by: java.lang.ClassNotFoundException: org.eclipse.ui.internal.ide.IDEWorkbenchAdvisor$2
 at org.eclipse.osgi.framework.internal.core.BundleLoa der.findClass(org.eclipse.osgi_3.2.2.R32x_v2007011 8.jar.so)
 at org.eclipse.osgi.framework.internal.core.BundleLoa der.findClass(org.eclipse.osgi_3.2.2.R32x_v2007011 8.jar.so)
 at org.eclipse.osgi.internal.baseadaptor.DefaultClass Loader.loadClass(org.eclipse.osgi_3.2.2.R32x_v2007 0118.jar.so)
 at java.lang.ClassLoader.loadClass(libgcj.so.81)
 at java.lang.Class.initializeClass(libgcj.so.81)
 ...11 more
 
 !ENTRY org.eclipse.osgi 4 0 2009-02-20 15:32:49.677
 !MESSAGE Application error
 !STACK 1
 java.lang.NoClassDefFoundError: org.eclipse.ui.internal.ide.IDEWorkbenchAdvisor
 at java.lang.Class.initializeClass(libgcj.so.81)
 at org.eclipse.ui.internal.ide.IDEApplication.run(org .eclipse.ui.ide_3.2.1.M20060915-1030.jar.so)
 at org.eclipse.core.internal.runtime.PlatformActivato r$1.run(org.eclipse.core.runtime_3.2.0.v20060603.j ar.so)
 at org.eclipse.core.runtime.internal.adaptor.EclipseA ppLauncher.runApplication(org.eclipse.osgi_3.2.2.R 32x_v20070118.jar.so)
 at org.eclipse.core.runtime.internal.adaptor.EclipseA ppLauncher.start(org.eclipse.osgi_3.2.2.R32x_v2007 0118.jar.so)
 at org.eclipse.core.runtime.adaptor.EclipseStarter.ru n(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
 at org.eclipse.core.runtime.adaptor.EclipseStarter.ru n(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
 at java.lang.reflect.Method.invoke(libgcj.so.81)
 at org.eclipse.core.launcher.Main.invokeFramework(Mai n.java:336)
 at org.eclipse.core.launcher.Main.basicRun(Main.java: 280)
 at org.eclipse.core.launcher.Main.run(Main.java:977)
 at org.eclipse.core.launcher.Main.main(Main.java:952)
 Caused by: java.lang.ClassNotFoundException: org.eclipse.ui.internal.ide.IDEWorkbenchAdvisor$2
 at org.eclipse.osgi.framework.internal.core.BundleLoa der.findClass(org.eclipse.osgi_3.2.2.R32x_v2007011 8.jar.so)
 at org.eclipse.osgi.framework.internal.core.BundleLoa der.findClass(org.eclipse.osgi_3.2.2.R32x_v2007011 8.jar.so)
 at org.eclipse.osgi.internal.baseadaptor.DefaultClass Loader.loadClass(org.eclipse.osgi_3.2.2.R32x_v2007 0118.jar.so)
 at java.lang.ClassLoader.loadClass(libgcj.so.81)
 at java.lang.Class.initializeClass(libgcj.so.81)
 ...11 more
 
 !ENTRY org.eclipse.osgi 2 0 2009-02-20 15:32:50.307
 !MESSAGE One or more bundles are not resolved because the following root constraints are not resolved:
 !SUBENTRY 1 org.eclipse.osgi 2 0 2009-02-20 15:32:50.307
 !MESSAGE Bundle [email]update@plugins/org.eclipse.tomcat.nl[/email]1_4.1.130.v200609270227/ was not resolved.
 !SUBENTRY 2 org.eclipse.tomcat.nl1 2 0 2009-02-20 15:32:50.307
 !MESSAGE Missing host org.eclipse.tomcat_[4.1.0,4.2.0).
 !SUBENTRY 1 org.eclipse.osgi 2 0 2009-02-20 15:32:50.307
 !MESSAGE Bundle [email]update@plugins/org.eclipse.tomcat.nl[/email]2a_4.1.130.v200609270227/ was not resolved.
 !SUBENTRY 2 org.eclipse.tomcat.nl2a 2 0 2009-02-20 15:32:50.308
 !MESSAGE Missing host org.eclipse.tomcat_[4.1.0,4.2.0).
 !SUBENTRY 1 org.eclipse.osgi 2 0 2009-02-20 15:32:50.308
 !MESSAGE Bundle [email]update@plugins/org.eclipse.tomcat.nlBidi[/email]_4.1.130.v200609270227/ was not resolved.
 !SUBENTRY 2 org.eclipse.tomcat.nlBidi 2 0 2009-02-20 15:32:50.308
 !MESSAGE Missing host org.eclipse.tomcat_[4.1.0,4.2.0).
 !SUBENTRY 1 org.eclipse.osgi 2 0 2009-02-20 15:32:50.308
 !MESSAGE Bundle [email]update@plugins/org.eclipse.tomcat.nl[/email]2_4.1.130.v200609270227/ was not resolved.
 !SUBENTRY 2 org.eclipse.tomcat.nl2 2 0 2009-02-20 15:32:50.308
 !MESSAGE Missing host org.eclipse.tomcat_[4.1.0,4.2.0).

---

