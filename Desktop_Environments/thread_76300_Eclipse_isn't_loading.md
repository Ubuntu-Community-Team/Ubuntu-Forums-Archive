---
title: "Eclipse isn't loading"
date: 2005-10-14
forum: Desktop Environments
---

### Post by astroboysoup on 2005-10-14
Hello

I just installed Eclipse from the Synaptic Package Manger on my iBook 500. (java1.4.2)

Downloaded and all went well but when I go to load the program I get a long list of plug in errors.

```
!SESSION 2005-10-15 11:57:04.673 -----------------------------------------------
eclipse.buildId=
java.fullversion=GNU libgcj 4.0.2 20050808 (prerelease) (Ubuntu 4.0.1-4ubuntu9)
BootLoader constants: OS=linux, ARCH=ppc, WS=gtk, NL=en_AU
Framework arguments:  
Command-line arguments:  -os linux -ws gtk -arch ppc 

!ENTRY org.eclipse.osgi 2005-10-15 11:57:16.912
!MESSAGE An error occurred while automatically activating bundle org.eclipse.ui.workbench (21).
!STACK 0
org.osgi.framework.BundleException: The activator org.eclipse.ui.internal.WorkbenchPlugin for bundle org.eclipse.ui.workbench is invalid
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator() (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start() (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start() (Unknown Source)
   at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(java.lang.String, boolean) (Unknown Source)
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.VMClassLoader.defineClass(java.lang.ClassLoader, java.lang.String, byte[], int, int, java.security.ProtectionDomain) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.ClassLoader.defineClass(java.lang.String, byte[], int, int, java.security.ProtectionDomain) (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.defineClass(java.lang.String, byte[], int, int, org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader$ClasspathEntry) (Unknown Source)
   at org.eclipse.core.runtime.adaptor.EclipseClassLoader.defineClass(java.lang.String, byte[], int, int, org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader$ClasspathEntry) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.findClassImpl(java.lang.String, org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader$ClasspathEntry) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.findClass(java.lang.String) (Unknown Source)
Caused by: java.lang.NoClassDefFoundError: while resolving class: org.eclipse.ui.plugin.AbstractUIPlugin
   at java.lang.VMClassLoader.transformException(java.lang.Class, java.lang.Throwable) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.VMClassLoader.resolveClass(java.lang.Class) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.initializeClass() (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.initializeClass() (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.newInstance() (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator() (Unknown Source)
   ...16 more
Caused by: java.lang.ClassNotFoundException: org.eclipse.swt.SWTError
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(java.lang.String, boolean) (Unknown Source)
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.forName(java.lang.String, boolean, java.lang.ClassLoader) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.VMClassLoader.resolveClass(java.lang.Class) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.initializeClass() (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.initializeClass() (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.newInstance() (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator() (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start() (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start() (Unknown Source)
   at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(java.lang.String, boolean) (Unknown Source)
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
Root exception:
java.lang.NoClassDefFoundError: while resolving class: org.eclipse.ui.plugin.AbstractUIPlugin
   at java.lang.VMClassLoader.transformException(java.lang.Class, java.lang.Throwable) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.VMClassLoader.resolveClass(java.lang.Class) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.initializeClass() (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.initializeClass() (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.newInstance() (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator() (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start() (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start() (Unknown Source)
   at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(java.lang.String, boolean) (Unknown Source)
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.VMClassLoader.defineClass(java.lang.ClassLoader, java.lang.String, byte[], int, int, java.security.ProtectionDomain) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.ClassLoader.defineClass(java.lang.String, byte[], int, int, java.security.ProtectionDomain) (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.defineClass(java.lang.String, byte[], int, int, org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader$ClasspathEntry) (Unknown Source)
   at org.eclipse.core.runtime.adaptor.EclipseClassLoader.defineClass(java.lang.String, byte[], int, int, org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader$ClasspathEntry) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.findClassImpl(java.lang.String, org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader$ClasspathEntry) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.DefaultClassLoader.findClass(java.lang.String) (Unknown Source)
Caused by: java.lang.ClassNotFoundException: org.eclipse.swt.SWTError
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(java.lang.String, boolean) (Unknown Source)
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.forName(java.lang.String, boolean, java.lang.ClassLoader) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.VMClassLoader.resolveClass(java.lang.Class) (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.initializeClass() (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.initializeClass() (/usr/lib/libgcj.so.6.0.0)
   at java.lang.Class.newInstance() (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator() (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start() (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start() (Unknown Source)
   at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.SingleSourcePackage.loadClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(java.lang.String, boolean) (Unknown Source)
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)

!ENTRY org.eclipse.osgi 2005-10-15 11:57:19.553
!MESSAGE An error occurred while automatically activating bundle org.eclipse.ui.ide (62).
!STACK 0
org.osgi.framework.BundleException: The activator org.eclipse.ui.internal.ide.IDEWorkbenchPlugin for bundle org.eclipse.ui.ide is invalid
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator() (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start() (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start() (Unknown Source)
   at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(java.lang.String, boolean) (Unknown Source)
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(java.lang.String) (Unknown Source)
   at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(org.osgi.framework.Bundle, java.lang.String, java.lang.Object, org.eclipse.core.internal.registry.ConfigurationElement, java.lang.String) (Unknown Source)
   at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(java.lang.String, java.lang.String, java.lang.Object, org.eclipse.core.internal.registry.ConfigurationElement, java.lang.String) (Unknown Source)
Caused by: java.lang.ClassNotFoundException: org.eclipse.ui.internal.ide.IDEWorkbenchPlugin
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(java.lang.String, boolean) (Unknown Source)
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator() (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start() (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start() (Unknown Source)
   at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(java.lang.String, boolean) (Unknown Source)
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(java.lang.String) (Unknown Source)
Root exception:
java.lang.ClassNotFoundException: org.eclipse.ui.internal.ide.IDEWorkbenchPlugin
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(java.lang.String, boolean) (Unknown Source)
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator() (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start() (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.start() (Unknown Source)
   at org.eclipse.core.runtime.adaptor.EclipseClassLoader.findLocalClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findLocalClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(java.lang.String, boolean) (Unknown Source)
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(java.lang.String) (Unknown Source)

!ENTRY org.eclipse.osgi 2005-10-15 11:57:21.430
!MESSAGE Application error
!STACK 1
org.eclipse.core.runtime.CoreException[1]: java.lang.ClassNotFoundException: org.eclipse.ui.internal.ide.IDEApplication
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.findClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.adaptor.core.AbstractClassLoader.loadClass(java.lang.String, boolean) (Unknown Source)
   at java.lang.ClassLoader.loadClass(java.lang.String) (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.osgi.framework.internal.core.BundleLoader.loadClass(java.lang.String) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(java.lang.String, boolean) (Unknown Source)
   at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(java.lang.String) (Unknown Source)
   at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(org.osgi.framework.Bundle, java.lang.String, java.lang.Object, org.eclipse.core.internal.registry.ConfigurationElement, java.lang.String) (Unknown Source)
   at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(java.lang.String, java.lang.String, java.lang.Object, org.eclipse.core.internal.registry.ConfigurationElement, java.lang.String) (Unknown Source)
   at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(java.lang.String) (Unknown Source)
   at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(java.lang.String) (Unknown Source)
   at org.eclipse.core.internal.runtime.PlatformActivator$1.run(java.lang.Object) (Unknown Source)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(java.lang.Object) (Unknown Source)
   at org.eclipse.core.runtime.adaptor.EclipseStarter.run(java.lang.String[], java.lang.Runnable) (Unknown Source)
   at java.lang.reflect.Method.invoke(java.lang.Object, java.lang.Object[]) (/usr/lib/libgcj.so.6.0.0)
   at org.eclipse.core.launcher.Main.invokeFramework(java.lang.String[], java.net.URL[]) (Unknown Source)

!ENTRY org.eclipse.osgi 2005-10-15 11:57:22.402
!MESSAGE Bundle update@plugins/org.eclipse.swt.gtk.linux.ppc_3.1.1.jar [23] was not resolved.

```

Sorry, alot of erros there. I've searched the forums and the wiki and parts of google but haven't been able to find something similar to this problem that I am having.

Any help would be much appreciated

I'm currently downloading the zip file from eclipse.org for the powerpc and tryinh a manual installation as perscribe in the ubuntu wiki. hopefully this helps... bu i would have assumed the Eclipse would have worked right out of the box for the new Breezy distro.

---

### Post by phobetron on 2005-10-15
I'm receiving the exact same error. It seems like there's a CLASSPATH problem, since it can't find any of its own classes. I'm not quite sure how the pkg maintainer put it together so I don't have much to go on. I noticed the /etc/eclipse/java_home file, and I think that's pretty odd but possibly useful if you want to run multiple VMs. Too bad eclipse won't work with any that I've tried.

I'm on an AMD64 machine, btw.

---

### Post by solstice on 2005-10-15
i was receiving similar errors. a quick way to fix this was to just copy the jre folder into the eclipse directory. I do think it is a path problem but haven't figured it out yet.

---

### Post by phobetron on 2005-10-15
The entire JRE? Would a symbolic link do?

From what I'm seeing, it seems like there are some jars missing, or aren't properly linked. org.eclipse.ui.internal.*.jar, org.eclipse.ui.plugin.*.jar and an architecture-specific org.eclipse.swt.gtk.linux.*arch*_3.1.1.jar.

---

### Post by codex22 on 2005-10-16
I installed java from Sun and set the JAVA_HOME environment variable accordingly.

That did it for me!

---

### Post by thava on 2006-01-13
I got the same problem

and now i try reinstall the sun-j2sdk1.5, still the same problem :(

anyone has idea abt whats wrong here?

Thanks
/ Thava

---

### Post by G99999k on 2008-01-11
I had the very same error log, and the only solution so far was as follows:

You have to purge and reinstall not only all the eclipse packages, but also libswt3.2-gtk-java and libswt3.2-gtk-jni, on which eclipse depends.

So, most likely, the eclipse installation messed up files included in gtk-java and gtk-jni, and that's why a reinstallation of eclipse only still gives that error. Any ideas which files that could be?

---

### Post by jordilin on 2008-01-12
I would download the latest tarball from eclipse site unzip it and run it from the command line. It works out of the box.

---

### Post by vsmolovik on 2008-03-06
I've fixed the same problem on my computer.

Hereby are the steps:
1) Remove your Eclipse by using "Synaptic Package Manager":
1.1) Select the following packages for "Complete Removal":
	eclipse,
	eclipse-jdt,
	eclipse-pde,
	eclipse-platform,
	eclipse-rcp,
	eclipse-source,
	libswt3.2-gtk-java
 and apply your changes. Actually, this is the list of those packages I've removed on my computer.
2) Be sure that /usr/lib/eclipse directory has been removed by uninstall or remove it manually;
3) Be sure that the /etc/eclipse directory has been removed by uninstall or remove it manually;
4) The trick is to remove your ~/eclipse directory manually after all aforementioned steps;

Now you are ready to install eclipse by using Add/Remove in the Ubuntu menu.

This method works for me, hope it works for you.

-Vlad.

---

