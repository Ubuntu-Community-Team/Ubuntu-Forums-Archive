---
title: "Eclipse doesn't start"
date: 2005-10-31
forum: Desktop Environments
---

### Post by No_Germs on 2005-10-31
-hope this is the right forum-
i've downloaded the eclipse sdk from the eclipse website. when i start it i, a little bit after i see the splash screen i get the message: "unable to read workbench state. workbench ui layout will be reset". 
i click ok and then eclipse appears, but with all the options (perspectives, new project) gone. when i try window->new window i get an error message "problems opening perspective 'org.eclipse.jdt.ui.javaperspective'.
i've tried downloading it again, from a different mirror... still it's the same problem.
does anyone know the reason?

---

### Post by Efwis on 2005-10-31
I dont' use Eclipse myself so I may be incorrect in this answer. If I am please let me know.

from what it appears to me to look like. I would say you need to install Java.

---

### Post by mloskot on 2005-11-01
Hi,

I also have have problem with eclipse - it does not start. I installed almost all eclipse-* packages + dependencies using Synaptic about 30 minutes ago.
When I try to start eclipse, then I get a message saying that error occured and I can see details in log file.

*Eclipse error message screenshot:*
[IMG]http://mateusz.loskot.net/chwila/eclipse-does-not-start.jpg[/IMG]

*And here is log file mentioned in the error message:*
```
!SESSION 2005-11-01 06:03:21.440 -----------------------------------------------
eclipse.buildId=
java.version=1.4.2-02
java.vendor=Blackdown Java-Linux Team
BootLoader constants: OS=linux, ARCH=x86_64, WS=gtk, NL=pl_PL
Framework arguments:  
Command-line arguments:  -os linux -ws gtk -arch x86_64 

!ENTRY org.eclipse.update.configurator 2005-11-01 06:03:22.919
!MESSAGE /usr/local/lib/eclipse/plugins is not a valid plugins directory.

!ENTRY org.eclipse.osgi 2005-11-01 06:03:26.327
!MESSAGE An error occurred while automatically activating bundle org.eclipse.ui.workbench (21).
!STACK 0
org.osgi.framework.BundleException: The activator org.eclipse.ui.internal.WorkbenchPlugin for bundle org.eclipse.ui.workbench is invalid
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:149)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:965)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:313)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:264)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(EclipseClassLoader.java:116)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:337)
	at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(SingleSourcePackage.java:37)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:386)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:350)
	at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(AbstractClassLoader.java:78)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:302)
	at java.lang.ClassLoader.defineClass0(Native Method)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:539)
	at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.defineClass(DefaultClassLoader.java:370)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.defineClass(EclipseClassLoader.java:233)
	at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.findClassImpl(DefaultClassLoader.java:343)
	at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.findClass(DefaultClassLoader.java:235)
	at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.findLocalClass(AbstractClassLoader.java:183)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.basicFindLocalClass(EclipseClassLoader.java:141)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(EclipseClassLoader.java:82)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:337)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:389)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:350)
	at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(AbstractClassLoader.java:78)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:275)
	at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:142)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:965)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:313)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:264)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(EclipseClassLoader.java:116)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:337)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:389)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:350)
	at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(AbstractClassLoader.java:78)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:275)
	at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(AbstractBundle.java:1248)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:152)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:142)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:129)
	at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:48)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:222)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:376)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:163)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:324)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:334)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:278)
	at org.eclipse.core.launcher.Main.run(Main.java:973)
	at org.eclipse.core.launcher.Main.main(Main.java:948)
Caused by: java.lang.NoClassDefFoundError: org/eclipse/swt/SWTError
	at java.lang.Class.getDeclaredConstructors0(Native Method)
	at java.lang.Class.privateGetDeclaredConstructors(Class.java:1618)
	at java.lang.Class.getConstructor0(Class.java:1930)
	at java.lang.Class.newInstance0(Class.java:278)
	at java.lang.Class.newInstance(Class.java:261)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:144)
	... 55 more
Root exception:
java.lang.NoClassDefFoundError: org/eclipse/swt/SWTError
	at java.lang.Class.getDeclaredConstructors0(Native Method)
	at java.lang.Class.privateGetDeclaredConstructors(Class.java:1618)
	at java.lang.Class.getConstructor0(Class.java:1930)
	at java.lang.Class.newInstance0(Class.java:278)
	at java.lang.Class.newInstance(Class.java:261)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:144)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:965)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:313)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:264)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(EclipseClassLoader.java:116)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:337)
	at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(SingleSourcePackage.java:37)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:386)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:350)
	at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(AbstractClassLoader.java:78)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:302)
	at java.lang.ClassLoader.defineClass0(Native Method)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:539)
	at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.defineClass(DefaultClassLoader.java:370)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.defineClass(EclipseClassLoader.java:233)
	at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.findClassImpl(DefaultClassLoader.java:343)
	at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.findClass(DefaultClassLoader.java:235)
	at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.findLocalClass(AbstractClassLoader.java:183)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.basicFindLocalClass(EclipseClassLoader.java:141)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(EclipseClassLoader.java:82)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:337)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:389)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:350)
	at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(AbstractClassLoader.java:78)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:275)
	at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:142)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:965)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:313)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:264)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(EclipseClassLoader.java:116)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:337)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:389)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:350)
	at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(AbstractClassLoader.java:78)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:275)
	at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(AbstractBundle.java:1248)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:152)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:142)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:129)
	at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:48)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:222)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:376)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:163)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:324)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:334)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:278)
	at org.eclipse.core.launcher.Main.run(Main.java:973)
	at org.eclipse.core.launcher.Main.main(Main.java:948)

!ENTRY org.eclipse.osgi 2005-11-01 06:03:26.331
!MESSAGE An error occurred while automatically activating bundle org.eclipse.ui.ide (62).
!STACK 0
org.osgi.framework.BundleException: The activator org.eclipse.ui.internal.ide.IDEWorkbenchPlugin for bundle org.eclipse.ui.ide is invalid
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:149)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:965)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:313)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:264)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(EclipseClassLoader.java:116)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:337)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:389)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:350)
	at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(AbstractClassLoader.java:78)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:275)
	at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(AbstractBundle.java:1248)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:152)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:142)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:129)
	at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:48)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:222)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:376)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:163)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:324)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:334)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:278)
	at org.eclipse.core.launcher.Main.run(Main.java:973)
	at org.eclipse.core.launcher.Main.main(Main.java:948)
Caused by: java.lang.NoClassDefFoundError: org/eclipse/ui/plugin/AbstractUIPlugin
	at java.lang.ClassLoader.defineClass0(Native Method)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:539)
	at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.defineClass(DefaultClassLoader.java:370)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.defineClass(EclipseClassLoader.java:233)
	at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.findClassImpl(DefaultClassLoader.java:343)
	at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.findClass(DefaultClassLoader.java:235)
	at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.findLocalClass(AbstractClassLoader.java:183)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.basicFindLocalClass(EclipseClassLoader.java:141)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(EclipseClassLoader.java:82)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:337)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:389)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:350)
	at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(AbstractClassLoader.java:78)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:275)
	at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:142)
	... 27 more
Root exception:
java.lang.NoClassDefFoundError: org/eclipse/ui/plugin/AbstractUIPlugin
	at java.lang.ClassLoader.defineClass0(Native Method)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:539)
	at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.defineClass(DefaultClassLoader.java:370)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.defineClass(EclipseClassLoader.java:233)
	at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.findClassImpl(DefaultClassLoader.java:343)
	at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.findClass(DefaultClassLoader.java:235)
	at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.findLocalClass(AbstractClassLoader.java:183)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.basicFindLocalClass(EclipseClassLoader.java:141)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(EclipseClassLoader.java:82)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:337)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:389)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:350)
	at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(AbstractClassLoader.java:78)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:275)
	at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:142)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:965)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:313)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:264)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(EclipseClassLoader.java:116)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:337)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:389)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:350)
	at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(AbstractClassLoader.java:78)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:275)
	at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(AbstractBundle.java:1248)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:152)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:142)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:129)
	at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:48)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:222)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:376)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:163)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:324)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:334)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:278)
	at org.eclipse.core.launcher.Main.run(Main.java:973)
	at org.eclipse.core.launcher.Main.main(Main.java:948)

!ENTRY org.eclipse.osgi 2005-11-01 06:03:26.334
!MESSAGE Application error
!STACK 1
org.eclipse.core.runtime.CoreException[1]: java.lang.ClassNotFoundException: org.eclipse.ui.internal.ide.IDEApplication
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:405)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:350)
	at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(AbstractClassLoader.java:78)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:275)
	at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(AbstractBundle.java:1248)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:152)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:142)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:129)
	at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:48)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:222)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:376)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:163)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:324)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:334)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:278)
	at org.eclipse.core.launcher.Main.run(Main.java:973)
	at org.eclipse.core.launcher.Main.main(Main.java:948)

!ENTRY org.eclipse.osgi 2005-11-01 06:03:26.338
!MESSAGE Bundle update@plugins/org.eclipse.swt.gtk.linux.x86_64_3.1.1.jar [23] was not resolved.

```

Is this a package bug? Should I report it to the [Malone]("https://launchpad.net/malone")?

Cheers

---

### Post by jvictor on 2005-11-01
Use sun Java. it'll work fine. Make the symlinks in /bin to point to ur sun java's java. nto ubuntus java

u need to also modify your .bashrc file and add these line

export JAVA_HOME=<your java hmoe dir>
export PATH=${JAVA_HOME}/bin:${PATH}

Chk my screenshot runnign eclipse 3.1 form eclispse and sun java

---

### Post by Efwis on 2005-11-01
[QUOTE=mloskot]Hi,

I also have have problem with eclipse - it does not start. I installed almost all eclipse-* packages + dependencies using Synaptic about 30 minutes ago.
When I try to start eclipse, then I get a message saying that error occured and I can see details in log file.

*Eclipse error message screenshot:*
[IMG]http://mateusz.loskot.net/chwila/eclipse-does-not-start.jpg[/IMG]

*And here is log file mentioned in the error message:*
```
!SESSION 2005-11-01 06:03:21.440 -----------------------------------------------
eclipse.buildId=
java.version=1.4.2-02
java.vendor=Blackdown Java-Linux Team
BootLoader constants: OS=linux, ARCH=x86_64, WS=gtk, NL=pl_PL
Framework arguments:  
Command-line arguments:  -os linux -ws gtk -arch x86_64 

!ENTRY org.eclipse.update.configurator 2005-11-01 06:03:22.919
!MESSAGE /usr/local/lib/eclipse/plugins is not a valid plugins directory.

!ENTRY org.eclipse.osgi 2005-11-01 06:03:26.327
!MESSAGE An error occurred while automatically activating bundle org.eclipse.ui.workbench (21).
!STACK 0
org.osgi.framework.BundleException: The activator org.eclipse.ui.internal.WorkbenchPlugin for bundle org.eclipse.ui.workbench is invalid
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:149)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:965)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:313)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:264)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(EclipseClassLoader.java:116)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:337)
	at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(SingleSourcePackage.java:37)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:386)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:350)
	at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(AbstractClassLoader.java:78)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:302)
	at java.lang.ClassLoader.defineClass0(Native Method)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:539)
	at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.defineClass(DefaultClassLoader.java:370)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.defineClass(EclipseClassLoader.java:233)
	at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.findClassImpl(DefaultClassLoader.java:343)
	at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.findClass(DefaultClassLoader.java:235)
	at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.findLocalClass(AbstractClassLoader.java:183)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.basicFindLocalClass(EclipseClassLoader.java:141)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(EclipseClassLoader.java:82)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:337)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:389)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:350)
	at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(AbstractClassLoader.java:78)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:275)
	at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:142)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:965)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:313)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:264)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(EclipseClassLoader.java:116)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:337)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:389)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:350)
	at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(AbstractClassLoader.java:78)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:275)
	at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(AbstractBundle.java:1248)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:152)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:142)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:129)
	at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:48)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:222)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:376)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:163)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:324)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:334)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:278)
	at org.eclipse.core.launcher.Main.run(Main.java:973)
	at org.eclipse.core.launcher.Main.main(Main.java:948)
Caused by: java.lang.NoClassDefFoundError: org/eclipse/swt/SWTError
	at java.lang.Class.getDeclaredConstructors0(Native Method)
	at java.lang.Class.privateGetDeclaredConstructors(Class.java:1618)
	at java.lang.Class.getConstructor0(Class.java:1930)
	at java.lang.Class.newInstance0(Class.java:278)
	at java.lang.Class.newInstance(Class.java:261)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:144)
	... 55 more
Root exception:
java.lang.NoClassDefFoundError: org/eclipse/swt/SWTError
	at java.lang.Class.getDeclaredConstructors0(Native Method)
	at java.lang.Class.privateGetDeclaredConstructors(Class.java:1618)
	at java.lang.Class.getConstructor0(Class.java:1930)
	at java.lang.Class.newInstance0(Class.java:278)
	at java.lang.Class.newInstance(Class.java:261)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:144)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:965)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:313)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:264)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(EclipseClassLoader.java:116)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:337)
	at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(SingleSourcePackage.java:37)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:386)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:350)
	at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(AbstractClassLoader.java:78)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:302)
	at java.lang.ClassLoader.defineClass0(Native Method)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:539)
	at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.defineClass(DefaultClassLoader.java:370)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.defineClass(EclipseClassLoader.java:233)
	at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.findClassImpl(DefaultClassLoader.java:343)
	at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.findClass(DefaultClassLoader.java:235)
	at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.findLocalClass(AbstractClassLoader.java:183)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.basicFindLocalClass(EclipseClassLoader.java:141)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(EclipseClassLoader.java:82)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:337)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:389)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:350)
	at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(AbstractClassLoader.java:78)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:275)
	at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:142)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:965)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:313)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:264)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(EclipseClassLoader.java:116)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:337)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:389)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:350)
	at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(AbstractClassLoader.java:78)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:275)
	at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(AbstractBundle.java:1248)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:152)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:142)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:129)
	at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:48)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:222)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:376)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:163)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:324)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:334)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:278)
	at org.eclipse.core.launcher.Main.run(Main.java:973)
	at org.eclipse.core.launcher.Main.main(Main.java:948)

!ENTRY org.eclipse.osgi 2005-11-01 06:03:26.331
!MESSAGE An error occurred while automatically activating bundle org.eclipse.ui.ide (62).
!STACK 0
org.osgi.framework.BundleException: The activator org.eclipse.ui.internal.ide.IDEWorkbenchPlugin for bundle org.eclipse.ui.ide is invalid
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:149)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:965)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:313)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:264)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(EclipseClassLoader.java:116)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:337)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:389)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:350)
	at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(AbstractClassLoader.java:78)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:275)
	at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(AbstractBundle.java:1248)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:152)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:142)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:129)
	at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:48)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:222)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:376)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:163)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:324)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:334)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:278)
	at org.eclipse.core.launcher.Main.run(Main.java:973)
	at org.eclipse.core.launcher.Main.main(Main.java:948)
Caused by: java.lang.NoClassDefFoundError: org/eclipse/ui/plugin/AbstractUIPlugin
	at java.lang.ClassLoader.defineClass0(Native Method)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:539)
	at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.defineClass(DefaultClassLoader.java:370)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.defineClass(EclipseClassLoader.java:233)
	at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.findClassImpl(DefaultClassLoader.java:343)
	at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.findClass(DefaultClassLoader.java:235)
	at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.findLocalClass(AbstractClassLoader.java:183)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.basicFindLocalClass(EclipseClassLoader.java:141)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(EclipseClassLoader.java:82)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:337)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:389)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:350)
	at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(AbstractClassLoader.java:78)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:275)
	at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:142)
	... 27 more
Root exception:
java.lang.NoClassDefFoundError: org/eclipse/ui/plugin/AbstractUIPlugin
	at java.lang.ClassLoader.defineClass0(Native Method)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:539)
	at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.defineClass(DefaultClassLoader.java:370)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.defineClass(EclipseClassLoader.java:233)
	at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.findClassImpl(DefaultClassLoader.java:343)
	at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.findClass(DefaultClassLoader.java:235)
	at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.findLocalClass(AbstractClassLoader.java:183)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.basicFindLocalClass(EclipseClassLoader.java:141)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(EclipseClassLoader.java:82)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:337)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:389)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:350)
	at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(AbstractClassLoader.java:78)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:275)
	at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:142)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:965)
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:313)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:264)
	at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(EclipseClassLoader.java:116)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(BundleLoader.java:337)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:389)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:350)
	at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(AbstractClassLoader.java:78)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:275)
	at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(AbstractBundle.java:1248)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:152)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:142)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:129)
	at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:48)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:222)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:376)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:163)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:324)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:334)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:278)
	at org.eclipse.core.launcher.Main.run(Main.java:973)
	at org.eclipse.core.launcher.Main.main(Main.java:948)

!ENTRY org.eclipse.osgi 2005-11-01 06:03:26.334
!MESSAGE Application error
!STACK 1
org.eclipse.core.runtime.CoreException[1]: java.lang.ClassNotFoundException: org.eclipse.ui.internal.ide.IDEApplication
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:405)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(BundleLoader.java:350)
	at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(AbstractClassLoader.java:78)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:235)
	at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(BundleLoader.java:275)
	at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:227)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(AbstractBundle.java:1248)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:152)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:142)
	at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:129)
	at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:48)
	at org.eclipse.core.internal.runtime.PlatformActivator$1.run(PlatformActivator.java:222)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:376)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:163)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:324)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:334)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:278)
	at org.eclipse.core.launcher.Main.run(Main.java:973)
	at org.eclipse.core.launcher.Main.main(Main.java:948)

!ENTRY org.eclipse.osgi 2005-11-01 06:03:26.338
!MESSAGE Bundle update@plugins/org.eclipse.swt.gtk.linux.x86_64_3.1.1.jar [23] was not resolved.

```

Is this a package bug? Should I report it to the [Malone]("https://launchpad.net/malone")?

Cheers[/QUOTE]
teh problem you are encountering is based on the JRE you are using. IE blackdown 1.4 jre.

The following is taken from the eclipse project website .[http://www.eclipse.org/eclipse/faq/eclipse-faq.html#users_3](http://www.eclipse.org/eclipse/faq/eclipse-faq.html#users_3)

> [color=red]**We recommend that you download and install a Java developer kit.**[/color] The developer kit will include a Java runtime that you can use to launch eclipse. Each build page contains a link to a page of suggested developer kit and Java runtime downloads that should work with the eclipse build. You can also find these links to commercial vendors that supply Java developer kits and Java runtime environments in the table below. You will need to decide for yourself which works best for you, and which licensing terms work best for you.
> Once you have installed a Java developer kit, you can use the -vm command line argument to launch eclipse.

so what it appears you need to do is the following. uninstall blackdown java 1.4, then go to sun Java and get their SDK. Directions are for installing this are in the [Official Ubununt Wiki.](https://wiki.ubuntu.com/RestrictedFormats?highlight=%28w32%29%7C%28codecs%29) Make sure you get the jdk not the jre update.
then see if you can get eclipse to work for you.

---

### Post by alcon on 2005-11-29
I just finished the instructions in the wiki for installing java 1.5 using apt-get install, make-jpkg and then dpkg.  It all seemed to work fine.  Eclipse however still has the error described in the first post.

---

### Post by jimmyp on 2005-11-29
[QUOTE=alcon]I just finished the instructions in the wiki for installing java 1.5 using apt-get install, make-jpkg and then dpkg.  It all seemed to work fine.  Eclipse however still has the error described in the first post.[/QUOTE]

go to a terminal and type java -version

If you don't get sun's java, man update-alternatives

---

### Post by Snam on 2006-07-13
Hello,

I get the following message when I try to start Eclipse:
"The custom VM you have chosen is not a valid executable"

When I type "java -version" I get the following output:
java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Client VM (build 1.5.0_06-b05, mixed mode, sharing)

That looks like the Sun Java to me.

How can I set the "custom VM"? Or: How can I solve this problem?

Thnx,

Snam

---

### Post by Ward Bergmans on 2006-07-13
> **Snam said:**
> 
I get the following message when I try to start Eclipse:
"The custom VM you have chosen is not a valid executable"

See: [http://www.ubuntuforums.org/showthread.php?t=82127&page=2]("http://www.ubuntuforums.org/showthread.php?t=82127&page=2")

Don't use the Ubuntu repository version, but download Eclipse directly from [www.eclipse.org](www.eclipse.org).

---

