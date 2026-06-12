---
title: "Gaim 2.0 BETA"
date: 2005-12-23
forum: Deferred/Invalid Requests
---

### Post by Gnobody on 2005-12-23
It seems really stable, I was wondering if somebody could backport it?

---

### Post by Stereotypical Rage on 2005-12-23
Doubt it till it's a final realize.

---

### Post by akurashy on 2005-12-23
i did my own deb if you want it :)

[http://ubuntu.akurashy.com/gaim-2.0.0_2.0.0-1_i386.deb](http://ubuntu.akurashy.com/gaim-2.0.0_2.0.0-1_i386.deb)

(optional of course, just bringing options! :D)

---

### Post by PtS on 2005-12-27
I just thought I should mension your .deb didn't work for me...
I'm sure there's a way to solve it but I don't care enough. About when will gaim 2.0 be ready anyway?

---

### Post by ricardo on 2005-12-27
[QUOTE=PtS]I just thought I should mension your .deb didn't work for me...
I'm sure there's a way to solve it but I don't care enough. About when will gaim 2.0 be ready anyway?[/QUOTE]

Try installing the libortp0 package. It works for me.

---

### Post by akurashy on 2005-12-27
[quote=ricardo]Try installing the libortp0 package. It works for me.[/quote]

that and libsamplerate0 i think

---

### Post by transgress on 2005-12-31
gaim 2.0 shouldn't be put up to replace gaim 1.5 yet by any means... they are still fine tuning it.  Lots of options are missing... which they did on purpose.  Not to mention many of the plugins were broken that were in apt.  Such as gaim-otr and guifications.  new guifications works but not the ones in apt.  gaim-otr is gonna need some recoding due to the menu at the bottom of the IM being gone.  Probably should let this stuff settle before we rush into making a replacement for 1.5

---

### Post by jdong on 2006-01-02
Beta software will not be backported... heck I'm not even sure I want to replace good ol GAIM 1.5 with 2.0 even once it comes out. I think we'll leave this to be sorted out by the Dapper release.

---

### Post by dave9191 on 2006-01-04
[QUOTE=akurashy]i did my own deb if you want it :)

[http://ubuntu.akurashy.com/gaim-2.0.0_2.0.0-1_i386.deb](http://ubuntu.akurashy.com/gaim-2.0.0_2.0.0-1_i386.deb)

(optional of course, just bringing options! :D)[/QUOTE]

After installing a couple missing libs on my comp the deb file worked. But it did replace the previous version of gaim installed, just a word of warning :) 

--
Dave

---

### Post by StarQuake on 2006-01-25
Could someone whip up an ubuntu package for beta2? I'm not yet into debian packaging

Would be great, beta1 is quiete stable already but I would like to see what's improved.

---

### Post by MighMoS on 2006-01-29
[QUOTE=StarQuake]Could someone whip up an ubuntu package for beta2? I'm not yet into debian packaging

Would be great, beta1 is quiete stable already but I would like to see what's improved.[/QUOTE]
I've got packages at [http://mighmos.org/packages.php](http://mighmos.org/packages.php)

---

### Post by potrick on 2006-01-30
debian package = ubuntu package, in this case. There is no specific ubuntu format. At the command line (applications->accessories->terminal) get to the folder where the package is and use the command "sudo dpkg -i package.deb" where package.deb is the package name. Hope this helps.

---

### Post by meijerpeter on 2006-03-17
Funny that GAIM (beta2.0) is more used on W32 platform than any other platform....see download status in Sourceforge....

---

### Post by hey560 on 2006-03-26
[QUOTE=MighMoS]I've got packages at [http://mighmos.org/packages.php](http://mighmos.org/packages.php)[/QUOTE]

Your packages are broken now with latest Dapper.  This is the dependency problem i get:

```
dpkg: dependency problems prevent configuration of gaim:
 gaim depends on libdbus-1-1 (>= 0.36.2); however:
  Package libdbus-1-1 is not installed.
 gaim depends on libdbus-glib-1-1 (>= 0.36.2); however:
  Package libdbus-glib-1-1 is not installed.
 gaim depends on libgnutls11 (>= 1.0.16); however:
  Package libgnutls11 is not installed.
```

The repositories now have libdbus-1-2 and libdbus-glib-1-2.  I guess I have to compile from source :-(.   Why oh why do the gaim developers made debian packages!

---

### Post by MighMoS on 2006-03-26
[QUOTE=hey560]Your packages are broken now with latest Dapper.  This is the dependency problem i get:

```
dpkg: dependency problems prevent configuration of gaim:
 gaim depends on libdbus-1-1 (>= 0.36.2); however:
  Package libdbus-1-1 is not installed.
 gaim depends on libdbus-glib-1-1 (>= 0.36.2); however:
  Package libdbus-glib-1-1 is not installed.
 gaim depends on libgnutls11 (>= 1.0.16); however:
  Package libgnutls11 is not installed.
```

The repositories now have libdbus-1-2 and libdbus-glib-1-2.  I guess I have to compile from source :-(.   Why oh why do the gaim developers made debian packages![/QUOTE]
Sorry, I wouldn't recommend installing my packages on Dapper Drake as they're compiled with Breezy Badger libs.  But cheer up, and new Gaim Beta (3) should be out pretty soon.

---

### Post by MighMoS on 2006-03-29
New -beta3 up at [http://ubuntuforums.org/showthread.php?p=871715#post871715](http://ubuntuforums.org/showthread.php?p=871715#post871715)

---

### Post by jjongsma on 2006-05-10
[QUOTE=PtS]I just thought I should mension your .deb didn't work for me...
I'm sure there's a way to solve it but I don't care enough. About when will gaim 2.0 be ready anyway?[/QUOTE]

Good question... they don't seem to have any release targets posted anywhere, and the devs were oh-so-helpful on IRC:

(09:23:23 AM) jjongsma: Is there anywhere I can find updates on the status of 2.0?
(09:24:21 AM) datallah: jjongsma: the main source of such information is the gaim website
(09:25:21 AM) jjongsma: datallah: checked there, haven't been any updates in february.  Do you know what the final release target is?
(09:28:49 AM) Paco-Paco: longer if we keep having to answer questions about it
(09:29:05 AM) Paco-Paco: but I'm sure the precise date and time is critical to your continued functioning

---

### Post by Rich930 on 2006-05-10
hey ppl! i have gaim 2.0.0 and yh its working really well!, this sounds stupid but im a dumbass, but what duz backport mean/?

---

