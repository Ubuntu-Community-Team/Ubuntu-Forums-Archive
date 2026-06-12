---
title: "Multiple Versions of Java, How?"
date: 2006-01-02
forum: Desktop Environments
---

### Post by flickerfly on 2006-01-02
I'm trying to run a program called DVArchive to interact with my ReplayTV Box. It requires Java 1.4.2, but I have Java 1.5.0_04, which results in the following error:

```
****************************************************************************
01/02 11:16:31.0114 [1.560] Notice: DVArchive V3.1 starting
01/02 11:16:31.0116 [1.580] DEBUG: OS Linux 2.6.12-10-386 (i386), Java 1.5.0_04, Sun Microsystems Inc. (49.0)
01/02 11:16:31.0117 [1.580] ERROR: DVArchive V3.1 is only certified for Java V1.4.2.
This system is using Java 1.5.0_04 which is not compatible.
Please install Java 1.4.2 to use DVArchive V3.1
```

Is there some way I can get Ubuntu/apt-get to install 2 versions of Sun Java and use 1.4.2 for DVArchive and the current one for everything else?

---

### Post by kperkins on 2006-01-02
Yes you can--I actually have 4 versions of java on my system.  You may have to add the path to 1.4.* when you configure DVArchive, unless you set 1.4.* as your default java.  (If you want to know how to do that post here, and I'll show you the command for that.)
Also 1.4.2 is the default version for Breezy, and you can get it through synaptic, or apt-get.  It's in the multiverse repos, and it's jre1.4 or j2sdk1.4 (i have both installed, but think you might only need the jre, for the runtime enviroment, and not sdk for development.)

---

### Post by flickerfly on 2006-01-02
Ah, that's a start, but this is the Blackdown version. I need Sun's Java for this particular program, probably something named sun-j2re1.4. Where do I get that?

---

### Post by kperkins on 2006-01-02
I'd try sun's site.  I think they archive the older versions.
Here: [http://java.sun.com/j2se/1.4.2/download.html](http://java.sun.com/j2se/1.4.2/download.html)

---

### Post by stuporglue on 2006-01-02
Are you *sure* you need Sun's version? The Blackdown version is much easier to install (just an apt-get), and it's worked with everything I've tried it with. 

If you do need the Sun version, or just prefer it, you can get it here: 
[http://java.sun.com/j2se/1.4.2/download.html](http://java.sun.com/j2se/1.4.2/download.html)  It's the J2SE JRE, under the thrid black bar from the top. 

You can try the Linux bin file installer, or use alien to convert the rpm to a deb package, then install that. 

That'll get it installed at least. :-)

Good luck!

---

### Post by flickerfly on 2006-01-02
For this, I really do need the Sun version, but it turned out that it was easy to download and install. I documented the steps over [here](http://josiah.ritchietribe.net/pmwiki/index.php?n=RePlay.DVArchive).

---

### Post by mattotoole on 2006-01-02
I'd be interested to know why you need an older version of Java, since they're supposed to be backward compatible.  One can never be sure, but I've never had a problem with older-version apps not running in a newer JRE.

Even writing Java apps I've learned to trust the compiler's version flags, instead of keeping old JDKs around.  So far, so good.

---

### Post by stuporglue on 2006-01-03
**Supposed to** is a strong word. :-) 

I personally need 1.4.2, but the blackdown version works for me. I use Irate Radio  ( [http://irate.sf.net](http://irate.sf.net) ) and it doesn't work with 1.5 yet.

---

### Post by measekite on 2007-11-02
> **kperkins said:**
> Yes you can--I actually have 4 versions of java on my system.  You may have to add the path to 1.4.* when you configure DVArchive, unless you set 1.4.* as your default java.  (If you want to know how to do that post here, and I'll show you the command for that.)
Also 1.4.2 is the default version for Breezy, and you can get it through synaptic, or apt-get.  It's in the multiverse repos, and it's jre1.4 or j2sdk1.4 (i have both installed, but think you might only need the jre, for the runtime enviroment, and not sdk for development.)


How do you set a path for Java for a program without having to change the default?

---

