---
title: "uDig GIS software installation"
date: 2006-11-17
forum: Education &amp; Science
---

### Post by geomantic8 on 2006-11-17
Has anyone installed [uDig]("http://udig.refractions.net") that would like to share their experience? 

I think my problem is pretty straightforward but being a java newbie, I don't know what I need to do to resolve it. I've installed the software correctly and it starts okay, but then exits with this error:

!ENTRY org.eclipse.core.runtime 4 0 2006-11-16 19:34:47.459
!MESSAGE FrameworkEvent.ERROR
!STACK 0
org.osgi.framework.BundleException: The bundle could not be resolved. Reason: Missing Constraint: Require-Bundle: org.eclipse.equinox.common; bundle-version="[3.2.0,4.0.0)"
	at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:294)
	at org.eclipse.osgi.framework.internal.core.AbstractBundle.resume(AbstractBundle.java:329)
	at org.eclipse.osgi.framework.internal.core.Framework.resumeBundle(Framework.java:1037)
	at org.eclipse.osgi.framework.internal.core.StartLevelManager.resumeBundles(StartLevelManager.java:573)
	at org.eclipse.osgi.framework.internal.core.StartLevelManager.incFWSL(StartLevelManager.java:495)
	at org.eclipse.osgi.framework.internal.core.StartLevelManager.doSetStartLevel(StartLevelManager.java:275)
	at org.eclipse.osgi.framework.internal.core.StartLevelManager.dispatchEvent(StartLevelManager.java:455)
	at org.eclipse.osgi.framework.eventmgr.EventManager.dispatchEvent(EventManager.java:189)
	at org.eclipse.osgi.framework.eventmgr.EventManager$EventThread.run(EventManager.java:291)

Any insight would be most welcome. Thanks in advance, 
g8

---

### Post by rgould on 2007-03-06
(Yes, this is almost 6 months old, but oh well :)

My guess is that the release you were using was broken? It looks like it has the wrong version of Eclipse's equinox declared, and it can't find what it is looking for. 

uDig on linux is just unzip and run (like eclipse)

---

### Post by dsmoney on 2008-06-21
[FONT="Verdana"]geomantic8:

I successfully installed Udig on an x86_64 machine:

**Install Java Advanced Imaging**

[https://jai.dev.java.net/binary-builds.html#Release_builds](https://jai.dev.java.net/binary-builds.html#Release_builds)

(INSTALL instructions)

[http://java.sun.com/products/java-media/jai/INSTALL-1_1_2.html](http://java.sun.com/products/java-media/jai/INSTALL-1_1_2.html)

Once this is done successfully the Udig package should just work...

[http://udig.refractions.net/download/](http://udig.refractions.net/download/)


However, I did not come across the error that you posted and cannot assist with a fix for it:(

Good Luck! 
[/FONT]

---

