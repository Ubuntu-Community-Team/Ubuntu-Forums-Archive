---
title: "AptanaStudio 1.1 Install Problems"
date: 2008-01-23
forum: Desktop Environments
---

### Post by pmiln099 on 2008-01-23
I don't know a heck of a lot about using my Ubuntu 7.10 and am having troubles installing the newest version of AptanaStudio 1.1. Below is the log file I get when double-clicking the executable from the extracted .zip download:

!SESSION 2008-01-23 10:08:22.886 -----------------------------------------------
eclipse.buildId=unknown
java.version=1.7.0
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_CA
Framework arguments:  Studio
Command-line arguments:  -os linux -ws gtk -arch x86 Studio

!ENTRY org.eclipse.equinox.common 4 0 2008-01-23 10:08:27.476
!MESSAGE FrameworkEvent.ERROR
!STACK 0
org.osgi.framework.BundleException: The bundle could not be resolved. Reason: Missing Constraint: Bundle-RequiredExecutionEnvironment: CDC-1.0/Foundation-1.0,J2SE-1.3
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:294)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.resume(AbstractBundle.java:329)
	at org.eclipse.osgi.framework.internal.core.Framework.resumeBundle(Framework.java:1046)
	at org.eclipse.osgi.framework.internal.core.StartLevelManager.resumeBundles(StartLevelManager.java:573)
	at org.eclipse.osgi.framework.internal.core.StartLevelManager.incFWSL(StartLevelManager.java:495)
	at org.eclipse.osgi.framework.internal.core.StartLevelManager.doSetStartLevel(StartLevelManager.java:275)
	at org.eclipse.osgi.framework.internal.core.StartLevelManager.dispatchEvent(StartLevelManager.java:455)
	at org.eclipse.osgi.framework.eventmgr.EventManager.dispatchEvent(EventManager.java:189)
	at org.eclipse.osgi.framework.eventmgr.EventManager$EventThread.run(EventManager.java:291)

!ENTRY org.eclipse.update.configurator 4 0 2008-01-23 10:08:27.483
!MESSAGE FrameworkEvent.ERROR
!STACK 0
org.osgi.framework.BundleException: The bundle could not be resolved. Reason: Missing Constraint: Bundle-RequiredExecutionEnvironment: J2SE-1.4,CDC-1.0/Foundation-1.0,J2SE-1.3
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:294)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.resume(AbstractBundle.java:329)
	at org.eclipse.osgi.framework.internal.core.Framework.resumeBundle(Framework.java:1046)
	at org.eclipse.osgi.framework.internal.core.StartLevelManager.resumeBundles(StartLevelManager.java:573)
	at org.eclipse.osgi.framework.internal.core.StartLevelManager.incFWSL(StartLevelManager.java:495)
	at org.eclipse.osgi.framework.internal.core.StartLevelManager.doSetStartLevel(StartLevelManager.java:275)
	at org.eclipse.osgi.framework.internal.core.StartLevelManager.dispatchEvent(StartLevelManager.java:455)
	at org.eclipse.osgi.framework.eventmgr.EventManager.dispatchEvent(EventManager.java:189)
	at org.eclipse.osgi.framework.eventmgr.EventManager$EventThread.run(EventManager.java:291)

!ENTRY org.eclipse.core.runtime 4 0 2008-01-23 10:08:27.491
!MESSAGE FrameworkEvent.ERROR
!STACK 0
org.osgi.framework.BundleException: The bundle could not be resolved. Reason: Missing Constraint: Bundle-RequiredExecutionEnvironment: CDC-1.0/Foundation-1.0,J2SE-1.3
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:294)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.resume(AbstractBundle.java:329)
	at org.eclipse.osgi.framework.internal.core.Framework.resumeBundle(Framework.java:1046)
	at org.eclipse.osgi.framework.internal.core.StartLevelManager.resumeBundles(StartLevelManager.java:573)
	at org.eclipse.osgi.framework.internal.core.StartLevelManager.incFWSL(StartLevelManager.java:495)
	at org.eclipse.osgi.framework.internal.core.StartLevelManager.doSetStartLevel(StartLevelManager.java:275)
	at org.eclipse.osgi.framework.internal.core.StartLevelManager.dispatchEvent(StartLevelManager.java:455)
	at org.eclipse.osgi.framework.eventmgr.EventManager.dispatchEvent(EventManager.java:189)
	at org.eclipse.osgi.framework.eventmgr.EventManager$EventThread.run(EventManager.java:291)

!ENTRY org.eclipse.osgi 4 0 2008-01-23 10:08:27.516
!MESSAGE Bundle [email]initial@reference:file:plugins/org.eclipse.equinox.common_3.2.0.v20060603.jar[/email]/ was not resolved.

!ENTRY org.eclipse.osgi 4 0 2008-01-23 10:08:27.521
!MESSAGE Bundle [email]initial@reference:file:plugins/org.eclipse.update.configurator_3.2.2.R32x_v20070111.jar[/email]/ was not resolved.

!ENTRY org.eclipse.osgi 4 0 2008-01-23 10:08:27.523
!MESSAGE Bundle [email]initial@reference:file:plugins/org.eclipse.core.runtime_3.2.0.v20060603.jar[/email]/ was not resolved.

!ENTRY org.eclipse.osgi 4 0 2008-01-23 10:08:27.839
!MESSAGE Application error
!STACK 1
java.lang.IllegalStateException: Unable to acquire application service. Ensure that the org.eclipse.core.runtime bundle is resolved and started (see config.ini).
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:65)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:400)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:177)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:623)
	at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
	at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
	at org.eclipse.core.launcher.Main.run(Main.java:977)
	at org.eclipse.core.launcher.Main.main(Main.java:952)

!ENTRY org.eclipse.osgi 2 0 2008-01-23 10:08:27.876
!MESSAGE One or more bundles are not resolved because the following root constraints are not resolved:
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-01-23 10:08:27.877
!MESSAGE Bundle [email]initial@reference:file:plugins/org.eclipse.update.configurator_3.2.2.R32x_v20070111.jar[/email]/ was not resolved.
!SUBENTRY 2 org.eclipse.update.configurator 2 0 2008-01-23 10:08:27.877
!MESSAGE Missing imported package javax.xml.parsers_0.0.0.
!SUBENTRY 2 org.eclipse.update.configurator 2 0 2008-01-23 10:08:27.878
!MESSAGE Missing imported package org.xml.sax_0.0.0.
!SUBENTRY 2 org.eclipse.update.configurator 2 0 2008-01-23 10:08:27.878
!MESSAGE Missing imported package org.w3c.dom_0.0.0.
!SUBENTRY 2 org.eclipse.update.configurator 2 0 2008-01-23 10:08:27.879
!MESSAGE Missing imported package org.xml.sax.helpers_0.0.0.
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-01-23 10:08:27.881
!MESSAGE Bundle [email]initial@reference:file:plugins/org.eclipse.core.runtime_3.2.0.v20060603.jar[/email]/ was not resolved.
!SUBENTRY 2 org.eclipse.core.runtime 2 0 2008-01-23 10:08:27.881
!MESSAGE Missing required bundle org.eclipse.core.contenttype_[3.2.0,4.0.0).
!SUBENTRY 2 org.eclipse.core.runtime 2 0 2008-01-23 10:08:27.882
!MESSAGE Missing required bundle org.eclipse.core.jobs_[3.2.0,4.0.0).
!SUBENTRY 2 org.eclipse.core.runtime 2 0 2008-01-23 10:08:27.882
!MESSAGE Missing required bundle org.eclipse.equinox.preferences_[3.2.0,4.0.0).
!SUBENTRY 2 org.eclipse.core.runtime 2 0 2008-01-23 10:08:27.882
!MESSAGE Missing required bundle org.eclipse.equinox.registry_[3.2.0,4.0.0).

!ENTRY org.eclipse.osgi 2 0 2008-01-23 10:08:27.892
!MESSAGE The following is a complete list of bundles which are not resolved, see the prior log entry for the root cause if it exists:
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-01-23 10:08:27.892
!MESSAGE Bundle [email]initial@reference:file:plugins/org.eclipse.equinox.common_3.2.0.v20060603.jar[/email]/ [1] was not resolved.
!SUBENTRY 2 org.eclipse.equinox.common 2 0 2008-01-23 10:08:27.893
!MESSAGE Missing Constraint: Bundle-RequiredExecutionEnvironment: CDC-1.0/Foundation-1.0,J2SE-1.3
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-01-23 10:08:27.893
!MESSAGE Bundle [email]initial@reference:file:plugins/org.eclipse.update.configurator_3.2.2.R32x_v20070111.jar[/email]/ [2] was not resolved.
!SUBENTRY 2 org.eclipse.update.configurator 2 0 2008-01-23 10:08:27.894
!MESSAGE Missing required bundle org.eclipse.equinox.common_[3.2.0,4.0.0).
!SUBENTRY 2 org.eclipse.update.configurator 2 0 2008-01-23 10:08:27.894
!MESSAGE Missing imported package javax.xml.parsers_0.0.0.
!SUBENTRY 2 org.eclipse.update.configurator 2 0 2008-01-23 10:08:27.894
!MESSAGE Missing imported package org.w3c.dom_0.0.0.
!SUBENTRY 2 org.eclipse.update.configurator 2 0 2008-01-23 10:08:27.895
!MESSAGE Missing imported package org.xml.sax_0.0.0.
!SUBENTRY 2 org.eclipse.update.configurator 2 0 2008-01-23 10:08:27.895
!MESSAGE Missing imported package org.xml.sax.helpers_0.0.0.
!SUBENTRY 1 org.eclipse.osgi 2 0 2008-01-23 10:08:27.896
!MESSAGE Bundle [email]initial@reference:file:plugins/org.eclipse.core.runtime_3.2.0.v20060603.jar[/email]/ [3] was not resolved.
!SUBENTRY 2 org.eclipse.core.runtime 2 0 2008-01-23 10:08:27.896
!MESSAGE Missing required bundle org.eclipse.equinox.common_[3.2.0,4.0.0).
!SUBENTRY 2 org.eclipse.core.runtime 2 0 2008-01-23 10:08:27.897
!MESSAGE Missing required bundle org.eclipse.core.jobs_[3.2.0,4.0.0).
!SUBENTRY 2 org.eclipse.core.runtime 2 0 2008-01-23 10:08:27.897
!MESSAGE Missing required bundle org.eclipse.equinox.registry_[3.2.0,4.0.0).
!SUBENTRY 2 org.eclipse.core.runtime 2 0 2008-01-23 10:08:27.897
!MESSAGE Missing required bundle org.eclipse.equinox.preferences_[3.2.0,4.0.0).
!SUBENTRY 2 org.eclipse.core.runtime 2 0 2008-01-23 10:08:27.898
!MESSAGE Missing required bundle org.eclipse.core.contenttype_[3.2.0,4.0.0).
!SUBENTRY 2 org.eclipse.core.runtime 2 0 2008-01-23 10:08:27.898
!MESSAGE Missing optionally required bundle org.eclipse.core.runtime.compatibility.auth_[3.2.0,4.0.0).

---

### Post by thermans on 2008-01-30
Did you ever get this working?

Looks like it can't find a java version it can use.  Did you install a new JRE?

From a terminal ("Applications/Accessories/Terminal") do:

```
update-alternatives --list java
```

And post the output here.

---

### Post by paranoid_humanoid on 2008-04-08
> **thermans said:**
> Did you ever get this working?

Looks like it can't find a java version it can use.  Did you install a new JRE?

From a terminal ("Applications/Accessories/Terminal") do:

```
update-alternatives --list java
```

And post the output here.

i've got the same problem.. mine outputs:

/usr/bin/gij-4.2
/usr/lib/jvm/java-7-icedtea/jre/bin/java
/usr/lib/jvm/java-6-sun/jre/bin/java

---

