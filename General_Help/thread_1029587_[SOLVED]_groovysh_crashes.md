---
title: "[SOLVED] groovysh crashes"
date: 2009-01-03
forum: General Help
---

### Post by fraktalek on 2009-01-03
Hi, I'm running Ubuntu 8.10, Intrepid, I've just installed groovy:

```

Package: groovy
New: yes
State: installed
Automatically installed: no
Version: 1.5.6-2
Priority: optional
Section: universe/devel
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Uncompressed Size: 2421k
Depends: antlr, libasm2-java, libbsf-java, libclassworlds-java (>= 1.0.1), libcommons-cli-java (>= 1.0), libcommons-collections3-java (>= 3.1), libcommons-logging-java (>=
         1.0.3), junit4, libmockobjects-java (>= 0.09), libmx4j-java (>= 2.0.1), libregexp-java (>= 1.2), libservlet2.4-java, libjline-java, libxpp3-java, libxstream-java,
         openjdk-6-jre-headless | java5-runtime-headless
Suggests: groovy-doc
Description: Agile dynamic language for the Java Virtual Machine

```

Running groovysh gives the following error:

```

~$ groovysh
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb749b7c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb749b891]
#2 /usr/lib/libX11.so.6(_XReply+0x254) [0x8c6d7494]
#3 /usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/i386/xawt/libmawt.so [0x8ca43dce]
#4 /usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/i386/xawt/libmawt.so [0x8ca2dd77]
#5 /usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/i386/xawt/libmawt.so [0x8ca2def3]
#6 /usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x26) [0x8ca2e136]
#7 [0xb14bb008]
#8 [0xb14b4b6b]
#9 [0xb14b4b6b]
#10 [0xb14b2236]
#11 /usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/i386/server/libjvm.so [0xb7744eec]
#12 /usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/i386/server/libjvm.so [0xb7914ae8]
#13 /usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/i386/server/libjvm.so [0xb7744d1f]
#14 /usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/i386/server/libjvm.so(JVM_DoPrivileged+0x32d) [0xb77a282d]
#15 /usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb745130d]
#16 [0xb14ba898]
#17 [0xb14b4a94]
#18 [0xb14b2236]
#19 /usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/i386/server/libjvm.so [0xb7744eec]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb749b7c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb749b96e]
#2 /usr/lib/libX11.so.6 [0x8c6d6619]
#3 /usr/lib/libX11.so.6(XGetVisualInfo+0x26) [0x8c6cc666]
#4 /usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/i386/xawt/libmawt.so [0x8ca2d0b9]
#5 /usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/i386/xawt/libmawt.so [0x8ca2d303]
#6 /usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/i386/xawt/libmawt.so [0x8ca2dfa1]
#7 /usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x26) [0x8ca2e136]
#8 [0xb14bb008]
#9 [0xb14b4b6b]
#10 [0xb14b4b6b]
#11 [0xb14b2236]
#12 /usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/i386/server/libjvm.so [0xb7744eec]
#13 /usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/i386/server/libjvm.so [0xb7914ae8]
#14 /usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/i386/server/libjvm.so [0xb7744d1f]
#15 /usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/i386/server/libjvm.so(JVM_DoPrivileged+0x32d) [0xb77a282d]
#16 /usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb745130d]
#17 [0xb14ba898]
#18 [0xb14b4a94]
#19 [0xb14b2236]
/usr/share/themes/Human/gtk-2.0/gtkrc:51: error: lexical error or unexpected token, expected valid token
java.lang.reflect.InvocationTargetException
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:585)
	at org.codehaus.groovy.tools.GroovyStarter.rootLoader(GroovyStarter.java:101)
	at org.codehaus.groovy.tools.GroovyStarter.main(GroovyStarter.java:130)
Caused by: java.lang.UnsupportedClassVersionError: Bad version number in .class file
	at java.lang.ClassLoader.defineClass1(Native Method)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:620)
	at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:124)
	at java.net.URLClassLoader.defineClass(URLClassLoader.java:260)
	at java.net.URLClassLoader.access$100(URLClassLoader.java:56)
	at java.net.URLClassLoader$1.run(URLClassLoader.java:195)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at org.codehaus.groovy.tools.RootLoader.oldFindClass(RootLoader.java:142)
	at org.codehaus.groovy.tools.RootLoader.loadClass(RootLoader.java:114)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
	at java.lang.Class.getDeclaredFields0(Native Method)
	at java.lang.Class.privateGetDeclaredFields(Class.java:2259)
	at java.lang.Class.getDeclaredFields(Class.java:1715)
	at org.codehaus.groovy.reflection.CachedClass$2.run(CachedClass.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.codehaus.groovy.reflection.CachedClass.getFields(CachedClass.java:214)
	at groovy.lang.MetaClassImpl.addFields(MetaClassImpl.java:1719)
	at groovy.lang.MetaClassImpl.inheritFields(MetaClassImpl.java:1714)
	at groovy.lang.MetaClassImpl.setupProperties(MetaClassImpl.java:1603)
	at groovy.lang.MetaClassImpl.addProperties(MetaClassImpl.java:2508)
	at groovy.lang.MetaClassImpl.initialize(MetaClassImpl.java:2479)
	at org.codehaus.groovy.runtime.metaclass.MetaClassRegistryImpl.getGlobalMetaClass(MetaClassRegistryImpl.java:253)
	at org.codehaus.groovy.runtime.metaclass.MetaClassRegistryImpl.access$100(MetaClassRegistryImpl.java:45)
	at org.codehaus.groovy.runtime.metaclass.MetaClassRegistryImpl$LocallyKnownClasses.getFromGlobal(MetaClassRegistryImpl.java:112)
	at org.codehaus.groovy.runtime.metaclass.MetaClassRegistryImpl$LocallyKnownClasses.getMetaClass(MetaClassRegistryImpl.java:88)
	at org.codehaus.groovy.runtime.metaclass.MetaClassRegistryImpl$MyThreadLocal.getMetaClass(MetaClassRegistryImpl.java:361)
	at org.codehaus.groovy.runtime.metaclass.MetaClassRegistryImpl.getMetaClass(MetaClassRegistryImpl.java:265)
	at org.codehaus.groovy.runtime.InvokerHelper.invokeConstructorOf(InvokerHelper.java:808)
	at org.codehaus.groovy.runtime.ScriptBytecodeAdapter.invokeNewN(ScriptBytecodeAdapter.java:230)
	at org.codehaus.groovy.tools.shell.Main.main(Main.groovy:121)
	... 6 more

Exception in thread "Thread-1" org.codehaus.groovy.runtime.InvokerInvocationException: java.lang.UnsupportedClassVersionError: Bad version number in .class file
	at org.codehaus.groovy.reflection.CachedMethod.invoke(CachedMethod.java:92)
	at groovy.lang.MetaMethod.doMethodInvoke(MetaMethod.java:230)
	at org.codehaus.groovy.runtime.metaclass.ClosureMetaClass.invokeMethod(ClosureMetaClass.java:248)
	at groovy.lang.MetaClassImpl.invokeMethod(MetaClassImpl.java:756)
	at groovy.lang.Closure.call(Closure.java:292)
	at groovy.lang.Closure.call(Closure.java:287)
	at groovy.lang.Closure.run(Closure.java:368)
	at java.lang.Thread.run(Thread.java:595)
Caused by: java.lang.UnsupportedClassVersionError: Bad version number in .class file
	at java.lang.ClassLoader.defineClass1(Native Method)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:620)
	at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:124)
	at java.net.URLClassLoader.defineClass(URLClassLoader.java:260)
	at java.net.URLClassLoader.access$100(URLClassLoader.java:56)
	at java.net.URLClassLoader$1.run(URLClassLoader.java:195)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:188)
	at org.codehaus.groovy.tools.RootLoader.oldFindClass(RootLoader.java:142)
	at org.codehaus.groovy.tools.RootLoader.loadClass(RootLoader.java:114)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:251)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:319)
	at org.codehaus.groovy.tools.shell.util.ANSI.detect(ANSI.java:48)
	at org.codehaus.groovy.tools.shell.util.ANSI.isDetected(ANSI.java:59)
	at org.codehaus.groovy.tools.shell.util.ANSI.isEnabled(ANSI.java:70)
	at org.codehaus.groovy.tools.shell.util.ANSI$Buffer.attrib(ANSI.java:225)
	at org.codehaus.groovy.tools.shell.util.ANSI$Renderer.evaluate(ANSI.java:313)
	at org.codehaus.groovy.tools.shell.util.ANSI$Renderer.render(ANSI.java:289)
	at org.codehaus.groovy.tools.shell.util.ANSI$RenderWriter.write(ANSI.java:378)
	at java.io.PrintWriter.print(PrintWriter.java:532)
	at java.io.PrintWriter.println(PrintWriter.java:669)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:585)
	at org.codehaus.groovy.reflection.CachedMethod.invoke(CachedMethod.java:86)
	at groovy.lang.MetaMethod.doMethodInvoke(MetaMethod.java:230)
	at groovy.lang.MetaClassImpl.invokeMethod(MetaClassImpl.java:912)
	at groovy.lang.MetaClassImpl.invokeMethod(MetaClassImpl.java:756)
	at org.codehaus.groovy.runtime.InvokerHelper.invokePojoMethod(InvokerHelper.java:766)
	at org.codehaus.groovy.runtime.InvokerHelper.invokeMethod(InvokerHelper.java:754)
	at org.codehaus.groovy.runtime.ScriptBytecodeAdapter.invokeMethodN(ScriptBytecodeAdapter.java:170)
	at org.codehaus.groovy.tools.shell.Main$_main_closure2.doCall(Main.groovy:109)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:585)
	at org.codehaus.groovy.reflection.CachedMethod.invoke(CachedMethod.java:86)
	at groovy.lang.MetaMethod.doMethodInvoke(MetaMethod.java:230)
	at org.codehaus.groovy.runtime.metaclass.ClosureMetaClass.invokeMethod(ClosureMetaClass.java:248)
	at org.codehaus.groovy.runtime.ScriptBytecodeAdapter.invokeMethodOnCurrentN(ScriptBytecodeAdapter.java:78)
	at org.codehaus.groovy.tools.shell.Main$_main_closure2.doCall(Main.groovy)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:585)

```

It looks like the groovy packages were compiled using Java 6. Shouldn't they be compiled using Java 5? Does the source code of Groovy really use Java 6?

Anyway, to switch to java 6 do the following:

```

update-java-alternatives -s java-6-sun

```

---

