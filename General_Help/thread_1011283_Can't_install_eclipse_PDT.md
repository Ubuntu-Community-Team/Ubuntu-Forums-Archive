---
title: "Can't install eclipse PDT"
date: 2008-12-14
forum: General Help
---

### Post by cshelswell on 2008-12-14
Hi,

I followed this tutorial to try and install eclipse PDT [http://ubuntuforums.org/showthread.php?p=3915455]("http://ubuntuforums.org/showthread.php?p=3915455") it's post #6

Eclipse seems to start up fine but then I get an error which fills out the log in my workspace folder. I'm running 64bit Intrepid. If anyone has any ideas or even a good tutorial for installing that'd be great. I've pasted my log below.

Many thanks
```

!SESSION 2008-12-14 09:59:49.969 -----------------------------------------------
eclipse.buildId=M20070212-1330
java.fullversion=GNU libgcj 4.3.2
BootLoader constants: OS=linux, ARCH=x86_64, WS=gtk, NL=en_GB
Command-line arguments:  -os linux -ws gtk -arch x86_64

!ENTRY org.eclipse.osgi 2 1 2008-12-14 09:59:55.997
!MESSAGE NLS missing message: initializer_error in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-12-14 09:59:55.998
!MESSAGE NLS missing message: fileInitializer_fileNotFound in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-12-14 09:59:55.998
!MESSAGE NLS missing message: fileInitializer_IOError in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-12-14 09:59:55.998
!MESSAGE NLS missing message: fileInitializer_missingFileName in: org.eclipse.core.internal.runtime.messages
!SESSION 2008-12-14 21:19:36.135 -----------------------------------------------
eclipse.buildId=M20070212-1330
java.fullversion=GNU libgcj 4.3.2
BootLoader constants: OS=linux, ARCH=x86_64, WS=gtk, NL=en_GB
Command-line arguments:  -os linux -ws gtk -arch x86_64

!ENTRY org.eclipse.osgi 2 1 2008-12-14 21:19:45.315
!MESSAGE NLS missing message: initializer_error in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-12-14 21:19:45.315
!MESSAGE NLS missing message: fileInitializer_fileNotFound in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-12-14 21:19:45.315
!MESSAGE NLS missing message: fileInitializer_IOError in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2008-12-14 21:19:45.315
!MESSAGE NLS missing message: fileInitializer_missingFileName in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 4 0 2008-12-14 21:19:48.297
!MESSAGE An error occurred while automatically activating bundle org.eclipse.core.resources (89).
!STACK 0
org.osgi.framework.BundleException: Exception in org.eclipse.core.internal.compatibility.PluginActivator.start() of bundle org.eclipse.core.resources.
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.util.SecureAction.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at java.lang.ClassLoader.loadClass(libgcj.so.90)
   at java.lang.Class.initializeClass(libgcj.so.90)
   at java.lang.Class.newInstance(libgcj.so.90)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.util.SecureAction.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at java.lang.ClassLoader.loadClass(libgcj.so.90)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.internal.registry.osgi.RegistryStrategyOSGI.createExecutableExtension(org.eclipse.equinox.registry_3.2.1.R32x_v20060814.jar.so)
   at org.eclipse.core.internal.registry.ExtensionRegistry.createExecutableExtension(org.eclipse.equinox.registry_3.2.1.R32x_v20060814.jar.so)
   at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(org.eclipse.equinox.registry_3.2.1.R32x_v20060814.jar.so)
   at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(org.eclipse.equinox.registry_3.2.1.R32x_v20060814.jar.so)
   at org.eclipse.core.internal.runtime.PlatformActivator$1.run(org.eclipse.core.runtime_3.2.0.v20060603.jar.so)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at java.lang.reflect.Method.invoke(libgcj.so.90)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
   at org.eclipse.core.launcher.Main.run(Main.java:977)
   at org.eclipse.core.launcher.Main.main(Main.java:952)
Caused by: java.lang.NoClassDefFoundError: org.eclipse.core.internal.resources.LocalMetaArea
   at java.lang.Class.initializeClass(libgcj.so.90)
   at org.eclipse.core.resources.ResourcesPlugin.startup(org.eclipse.core.resources_3.2.2.R32x_v20061218.jar.so)
   at org.eclipse.core.internal.compatibility.PluginActivator.start(org.eclipse.core.runtime.compatibility_3.1.100.v20060603.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl$2.run(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at java.security.AccessController.doPrivileged(libgcj.so.90)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   ...45 more
Caused by: java.lang.OutOfMemoryError
   <<No stacktrace available>>
Root exception:
java.lang.NoClassDefFoundError: org.eclipse.core.internal.resources.LocalMetaArea
   at java.lang.Class.initializeClass(libgcj.so.90)
   at org.eclipse.core.resources.ResourcesPlugin.startup(org.eclipse.core.resources_3.2.2.R32x_v20061218.jar.so)
   at org.eclipse.core.internal.compatibility.PluginActivator.start(org.eclipse.core.runtime.compatibility_3.1.100.v20060603.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl$2.run(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at java.security.AccessController.doPrivileged(libgcj.so.90)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.util.SecureAction.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at java.lang.ClassLoader.loadClass(libgcj.so.90)
   at java.lang.Class.initializeClass(libgcj.so.90)
   at java.lang.Class.newInstance(libgcj.so.90)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.util.SecureAction.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at java.lang.ClassLoader.loadClass(libgcj.so.90)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.internal.registry.osgi.RegistryStrategyOSGI.createExecutableExtension(org.eclipse.equinox.registry_3.2.1.R32x_v20060814.jar.so)
   at org.eclipse.core.internal.registry.ExtensionRegistry.createExecutableExtension(org.eclipse.equinox.registry_3.2.1.R32x_v20060814.jar.so)
   at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(org.eclipse.equinox.registry_3.2.1.R32x_v20060814.jar.so)
   at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(org.eclipse.equinox.registry_3.2.1.R32x_v20060814.jar.so)
   at org.eclipse.core.internal.runtime.PlatformActivator$1.run(org.eclipse.core.runtime_3.2.0.v20060603.jar.so)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at java.lang.reflect.Method.invoke(libgcj.so.90)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
   at org.eclipse.core.launcher.Main.run(Main.java:977)
   at org.eclipse.core.launcher.Main.main(Main.java:952)
Caused by: java.lang.OutOfMemoryError
   <<No stacktrace available>>

!ENTRY org.eclipse.osgi 4 0 2008-12-14 21:19:59.624
!MESSAGE An error occurred while automatically activating bundle org.eclipse.core.resources (89).
!STACK 0
org.osgi.framework.BundleException: Exception in org.eclipse.core.internal.compatibility.PluginActivator.start() of bundle org.eclipse.core.resources.
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.util.SecureAction.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at java.lang.ClassLoader.loadClass(libgcj.so.90)
   at java.lang.Class.initializeClass(libgcj.so.90)
   at org.eclipse.ui.internal.ide.IDEApplication.run(org.eclipse.ui.ide_3.2.1.M20060915-1030.jar.so)
   at org.eclipse.core.internal.runtime.PlatformActivator$1.run(org.eclipse.core.runtime_3.2.0.v20060603.jar.so)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at java.lang.reflect.Method.invoke(libgcj.so.90)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
   at org.eclipse.core.launcher.Main.run(Main.java:977)
   at org.eclipse.core.launcher.Main.main(Main.java:952)
Caused by: java.lang.NoClassDefFoundError: org.eclipse.core.internal.resources.LocalMetaArea
   at java.lang.Class.initializeClass(libgcj.so.90)
   at org.eclipse.core.resources.ResourcesPlugin.startup(org.eclipse.core.resources_3.2.2.R32x_v20061218.jar.so)
   at org.eclipse.core.internal.compatibility.PluginActivator.start(org.eclipse.core.runtime.compatibility_3.1.100.v20060603.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl$2.run(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at java.security.AccessController.doPrivileged(libgcj.so.90)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   ...25 more
Root exception:
java.lang.NoClassDefFoundError: org.eclipse.core.internal.resources.LocalMetaArea
   at java.lang.Class.initializeClass(libgcj.so.90)
   at org.eclipse.core.resources.ResourcesPlugin.startup(org.eclipse.core.resources_3.2.2.R32x_v20061218.jar.so)
   at org.eclipse.core.internal.compatibility.PluginActivator.start(org.eclipse.core.runtime.compatibility_3.1.100.v20060603.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl$2.run(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at java.security.AccessController.doPrivileged(libgcj.so.90)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.util.SecureAction.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.preFindLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at java.lang.ClassLoader.loadClass(libgcj.so.90)
   at java.lang.Class.initializeClass(libgcj.so.90)
   at org.eclipse.ui.internal.ide.IDEApplication.run(org.eclipse.ui.ide_3.2.1.M20060915-1030.jar.so)
   at org.eclipse.core.internal.runtime.PlatformActivator$1.run(org.eclipse.core.runtime_3.2.0.v20060603.jar.so)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at java.lang.reflect.Method.invoke(libgcj.so.90)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
   at org.eclipse.core.launcher.Main.run(Main.java:977)
   at org.eclipse.core.launcher.Main.main(Main.java:952)

!ENTRY org.eclipse.osgi 4 0 2008-12-14 21:19:59.779
!MESSAGE Application error
!STACK 1
java.lang.NoClassDefFoundError: org.eclipse.ui.internal.ide.IDEWorkbenchAdvisor
   at java.lang.Class.initializeClass(libgcj.so.90)
   at org.eclipse.ui.internal.ide.IDEApplication.run(org.eclipse.ui.ide_3.2.1.M20060915-1030.jar.so)
   at org.eclipse.core.internal.runtime.PlatformActivator$1.run(org.eclipse.core.runtime_3.2.0.v20060603.jar.so)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at java.lang.reflect.Method.invoke(libgcj.so.90)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
   at org.eclipse.core.launcher.Main.run(Main.java:977)
   at org.eclipse.core.launcher.Main.main(Main.java:952)
Caused by: java.lang.ClassNotFoundException: org.eclipse.core.resources.IWorkspaceRoot
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(org.eclipse.osgi_3.2.2.R32x_v20070118.jar.so)
   at java.lang.ClassLoader.loadClass(libgcj.so.90)
   at java.lang.Class.initializeClass(libgcj.so.90)
   ...11 more

```

---

