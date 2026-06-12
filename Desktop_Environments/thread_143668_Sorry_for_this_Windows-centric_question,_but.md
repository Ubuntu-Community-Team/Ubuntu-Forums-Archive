---
title: "Sorry for this Windows-centric question, but"
date: 2006-03-12
forum: Desktop Environments
---

### Post by OfficeLinebacker on 2006-03-12
Is there an Ubuntu program that is the equivalent of PC-Wizard?
 
I'd like a one-stop way fo seeing all the system hardware specs.

---

### Post by kaamos on 2006-03-12
[http://gnomefiles.org/app.php?soft_id=626](http://gnomefiles.org/app.php?soft_id=626)

[IMG]http://gsysinfo.sourceforge.net/project/pix/sysinfo_cpu_screen.png[/IMG]

---

### Post by OfficeLinebacker on 2006-03-12
can you sudo apt-get sysinfo or is it a manual install?
 
BTW, thanks!

---

### Post by matthew on 2006-03-12
[quote=OfficeLinebacker]can you sudo apt-get sysinfo or is it a manual install?
 
BTW, thanks![/quote]Looking here ([http://packages.ubuntu.com/](http://packages.ubuntu.com/)) I see that it is available for Dapper in the universe repository. However, it is not available in the repos for Breezy or earlier so unless you are using Dapper it will be a manual install.

---

### Post by OfficeLinebacker on 2006-03-12
So this is the kind of thing that might one day turn into a backport?

---

### Post by matthew on 2006-03-12
[quote=OfficeLinebacker]So this is the kind of thing that might one day turn into a backport?[/quote]Potentially. This would be the place to ask about the possibility: [http://ubuntuforums.org/forumdisplay.php?f=79](http://ubuntuforums.org/forumdisplay.php?f=79)

---

### Post by OfficeLinebacker on 2006-03-13
OK, before I make a boneheaded move over there, I see this criterion:
 
**New packages MUST build cleanly from Debian source archives**. That is, "apt-get build-dep PACKAGE; apt-get source -b PACKAGE" **must** produce a working package in order for it to be backportable. No 'hacking dependencies' or 'skipping build-dep' or any force flags of any kind. 
 
Can I assume that the fact that it's available for Dapper means this is true?

---

### Post by meborc on 2006-03-13
yes... if it is in dapper, then it is probably very easy (or very difficult) to port it back to breezy :mrgreen: ...

i think the request is acceptable so go ahead

---

### Post by OfficeLinebacker on 2006-03-13
Thanks!

---

### Post by Hamman on 2006-03-16
Does anybody know if something like this exists for KDE? Not that I mind ```
cat /proc/cpuinfo
``` and friends, but it would be nice to have.

---

### Post by JDavid5381 on 2006-03-16
I read your post and I've been wondering about the same thing for a while now.  Could someone point me in the right direction or provide a link on how to manually install something (I'm using breezy), this software in particular? I just learned how to install stuff using the whole "sudo apt-get" method.  I need more info on this whole "manually installing something" business.

-James

---

### Post by Ramses de Norre on 2006-03-16
You'll need to compile it from source, basically you'll download a sourcefile, untar it, cd to the dir, run ./configure, make, sudo make install.
But it sometimes takes extra options/dependencies that are described in the read me.
Also always look very closely to the output of ./configure, things that aren't ok in there should be fixed before running make. (wont work otherwise)

---

### Post by Sef on 2006-03-16
> You'll need to compile it from source....

Before compiling, you will need to download build-essentials; otherwise, the compiling won't work.

To download build-essentials:

sudo apt-get update

sudo apt-get install build-essentials

---

### Post by nalmeth on 2006-03-16
This looks cool, will check out on my dapper laptop. 
I don't know what PC-Wizard is. Is it basically the device manager for XP? Gnome's device manager should be able to tell you some specs about your hardware etc. Maybe not what you're looking for? Dunno

---

### Post by OfficeLinebacker on 2006-03-16
PC Wizard is from the makers of cpuz.  It's like SiSoft Sandra in that it identifies all your hardware for you, and lets you run some benchmarks.

I just wanted to verify if my chipset was Intel 810 or 810e, and I just ended up sudo apt-getting hardinfo and that did the trick well enough.

I'll just install Dapper going forward.

---

