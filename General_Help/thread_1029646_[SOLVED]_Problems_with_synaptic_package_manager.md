---
title: "[SOLVED] Problems with synaptic package manager"
date: 2009-01-03
forum: General Help
---

### Post by blurplelove on 2009-01-03
Every time I try to open synaptic, it gives me this error message:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->opem() failed, please report.

When I enter 'dpkg --configure -a' into the terminal it gives me the message:
dpkg: requested operation requires superuser priveledge

I already have all the priveledges though..  I don't even know if that is how I'm supposed to manually run it.. I'm confused. XD
How do I fix it?

Hopefully someone can help me with this.
& Thanks in advance! :)

---

### Post by abn91c on 2009-01-03
> **blurplelove said:**
> Every time I try to open synaptic, it gives me this error message:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->opem() failed, please report.

When I enter 'dpkg --configure -a' into the terminal it gives me the message:
dpkg: requested operation requires superuser priveledge

I already have all the priveledges though..  I don't even know if that is how I'm supposed to manually run it.. I'm confused. XD
How do I fix it?

Hopefully someone can help me with this.
& Thanks in advance! :)
**[COLOR="Red"]sudo dpkg --configure -a[/COLOR]**

---

### Post by blurplelove on 2009-01-03
Ooooh! Thanks again, abn91c! :)

---

### Post by bleaksquid on 2009-01-25
Hey There,

I'm having the same problem, but after I run the command I get this spiel:

"Setting up rhino (1.6.R7-2) ...

dpkg: dependency problems prevent configuration of openjdk-6-jre:
 openjdk-6-jre depends on openjdk-6-jre-headless (>= 6b11-2ubuntu2); however:
  Version of openjdk-6-jre-headless on system is 6b09-0ubuntu2.
dpkg: error processing openjdk-6-jre (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openjdk-6-jre-lib:
 openjdk-6-jre-lib depends on openjdk-6-jre-headless (>= 6b11); however:
  Version of openjdk-6-jre-headless on system is 6b09-0ubuntu2.
dpkg: error processing openjdk-6-jre-lib (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of openjdk-6-jre-headless:
 openjdk-6-jre-headless depends on openjdk-6-jre-lib (>= 6b09-0ubuntu2); however:
  Package openjdk-6-jre-lib is not configured yet.
dpkg: error processing openjdk-6-jre-headless (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 openjdk-6-jre
 openjdk-6-jre-lib
 openjdk-6-jre-headless"


What the heck is this? :-s

---

### Post by mb_webguy on 2009-01-25
You're not meeting the dependencies for that package.  You need openjdk-6-jre-headless version 6b11-2ubuntu2 or better, and you have version 6b09-0ubuntu2.  You need to download and install a more recent version of openjdk-6-jre-headless.

---

### Post by bleaksquid on 2009-01-25
> **mb_webguy said:**
> You're not meeting the dependencies for that package.  You need openjdk-6-jre-headless version 6b11-2ubuntu2 or better, and you have version 6b09-0ubuntu2.  You need to download and install a more recent version of openjdk-6-jre-headless.

Thank you for the quick reply. Sorry if this is a noobish question but where do I find the download for this and how exactly do I download it? I'm not knowledgeable about downloading items in Linux.

---

### Post by bleaksquid on 2009-01-25
Anyone? Bueller?

---

### Post by MaindotC on 2009-02-17
You type:
```

sudo apt-get install openjdk-6-jre-headless

```
but don't bother because that just leads to a recursive loop of dependency errors.

---

