---
title: "What is Mono?"
date: 2009-06-11
forum: General Help
---

### Post by pbhill on 2009-06-11
I have found a process running that consumes about 40% of my CPU called Mono.
What is this and why is it suddenly using so much of my CPU?

---

### Post by ActiveFrost on 2009-06-11
About [Mono]("http://www.mono-project.com/About") :
> Mono, the open source development platform based on the .NET framework, allows developers to build Linux and cross-platform applications with improved developer productivity.

In other words, do you use Mono ( .NET development tool ) ?

---

### Post by directhex on 2009-06-11
Mono is an application framework, used by some apps (e.g. Tomboy, F-Spot, GNOME Do)

This is highly likely to be a bug in an application you're running. One culprit I've heard causing this in the past is Drapes - it may be something else. Without knowing exactly which app you're running, it's hard to propose a fix.

---

### Post by colau on 2009-06-11
> **pbhill said:**
> I have found a process running that consumes about 40% of my CPU called Mono.
What is this and why is it suddenly using so much of my CPU?
[mono]("http://en.wikipedia.org/wiki/Mono_(software)")

---

### Post by Simian Man on 2009-06-11
In addition to the apps DirectHex listed, Banshee is another Mono app that can cause high CPU usage.  What apps do you have running.

---

### Post by pbhill on 2009-06-12
> **ActiveFrost said:**
> About [Mono]("http://www.mono-project.com/About") :


In other words, do you use Mono ( .NET development tool ) ?

No. Never heard of it.

---

### Post by pbhill on 2009-06-12
Actually I have been trying to run Drapes, but it hasn't worked properly since installing 9.04.  I'll bet that's it...

---

### Post by jbruced on 2009-06-12
> **directhex said:**
> Mono is an application framework, used by some apps (e.g. Tomboy, F-Spot, GNOME Do)

This is highly likely to be a bug in an application you're running. One culprit I've heard causing this in the past is Drapes - it may be something else. Without knowing exactly which app you're running, it's hard to propose a fix.

You are a guru dripping with Ubuntu, I learned something new from you today.

Good call. :D

---

### Post by directhex on 2009-06-12
> **pbhill said:**
> Actually I have been trying to run Drapes, but it hasn't worked properly since installing 9.04.  I'll bet that's it...

I'd bet that's it too. I'd love to know WHY it happens though, so it can be fixed.

---

### Post by gjtoth on 2009-06-13
More importantly to me is:  Is Mono mandatory?  Can I remove/uninstall it without bringing down the system.  It seems to react adversely to a few apps that used to run flawlessly in previous versions of Ubuntu.

---

### Post by ktrnka on 2009-06-13
If you remove Mono, it will take out tomboy and F-Spot with it but it will leave your system intact and no harm will be done.

---

### Post by directhex on 2009-06-13
> **gjtoth said:**
> More importantly to me is:  Is Mono mandatory?  Can I remove/uninstall it without bringing down the system.  It seems to react adversely to a few apps that used to run flawlessly in previous versions of Ubuntu.

Remove libmono0 and mono-common to remove Mono and all Mono apps.

---

