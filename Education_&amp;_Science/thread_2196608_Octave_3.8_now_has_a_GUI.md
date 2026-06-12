---
title: "Octave 3.8 now has a GUI"
date: 2013-12-30
forum: Education &amp; Science
---

### Post by PC_load_letter on 2013-12-30
I read about it this morning at Slahdot.org (reporting what Phronix had). Long story short, I compiled it on my meager Asus laptop (dual Celeron) w/ Ubuntu 12.04, took about an hour to compile. GUI looks very similar to the Qt version. The gui will run by default in version 4.0. To compile & install, I followed the instructions here: 
[http://blogs.bu.edu/mhirsch/2013/12/compiling-octave-3-8/](http://blogs.bu.edu/mhirsch/2013/12/compiling-octave-3-8/)

This is how it looks like, I say nice work Octave team, finally a workable gui. They have some debugging features already implemented, will have to test it and report, so far I think it's awesome.
[IMG]http://img844.imageshack.us/img844/7038/h2uo.png[/IMG]

---

### Post by mJayk on 2014-01-02
Saw this a few days back, been waiting for this for ages. Thanks for the compile link that was very helpful wasn't able to get it to compile when I first tried it.

---

### Post by david-cortes-o on 2014-01-03
Thanks for the info, I could install it perfectly on Ubuntu 13.04. I hope they release a PPA soon :)

---

### Post by PC_load_letter on 2014-01-06
No problem. I wouldn't hold my breath for an official PPA, iirc, it never existed.

I am experiencing a minor bug that I'm afraid it could be unique to Ubuntu+Unity. When I use CTRL+ALT+arrows to change workspaces and come back to the Octave GUI workspace, I find that Octave had lost the window focus and I have to click on the "Editor" tab then "Command window" to get it back. Without the window focus, the global menu shows the menu of the terminal instead that of the Octave GUI. Can anyone confirm this?

---

### Post by monkeybrain20122 on 2014-01-06
> **PC_load_letter said:**
> 
I am experiencing a minor bug that I'm afraid it could be unique to Ubuntu+Unity. When I use CTRL+ALT+arrows to change workspaces and come back to the Octave GUI workspace, I find that Octave had lost the window focus and I have to click on the "Editor" tab then "Command window" to get it back. Without the window focus, the global menu shows the menu of the terminal instead that of the Octave GUI. Can anyone confirm this?

Yes I can confirm it. Using edge flip to switch workspaces gets same result, a minor anonyance. 

A more major one is I can't build shogun-octave. The (shogun) bug is   described here [https://bugzilla.redhat.com/show_bug.cgi?id=1047051](https://bugzilla.redhat.com/show_bug.cgi?id=1047051) 

**Edited: **I tried to disable the global menu for octave gui by starting octave with
```
octave --force-gui UBUNTU_MENUPROXY=0
```
Octave simply crashed.Not sure if this is the right way of doing it. 

If you are on 12.04 you can remove the global menu altogether. In 13.04 and up gnome applications like nautilus and evince will be missing their menus (or rather a part of them) if you do.

---

### Post by PC_load_letter on 2014-01-06
Thanks monkeybrain20122. The window focus bug is minor I agree, I am oblivious to shogun-octave though, but it looks much more serious. 

I hope the next Ubuntu release, 14.04, will have the 3.8 in the repos so that many more Ubuntu users can install it and test it for bugs to make sure any Ubuntu specific ones get fixed before reaching the milestone release, ver. 4.0.

---

### Post by monkeybrain20122 on 2014-01-06
> **david-cortes-o said:**
> Thanks for the info, I could install it perfectly on Ubuntu 13.04. I hope they release a PPA soon :)

Just found one
[https://launchpad.net/~gabriel1984sibiu/+archive/aplicatii](https://launchpad.net/~gabriel1984sibiu/+archive/aplicatii)

It is quite easy to compile once have all the prerequsites installed (see the octave wiki), just "./configure, make, sudo make install" (or "sudo checkinstall", which I prefer), but it took me an hour for 'make' and need to add the command "export JAVA_HOME=pathtojdk" before ./configure to get rid of the complaint that JAVA_HOME is not set.

I think Trusty will still come with 3.6.4, though, as they would have to wait for Debian to package it and Debian is slow. Look at how long it took gimp 2.8 to make it to the repo and gimp has much higher profile than Octave.

---

### Post by monkeybrain20122 on 2014-01-06
Some packages from octave forge are not installable, e.g io hence packages that depend on it such as statistics. Guess just have to wait for the octave forge packages to update..

---

