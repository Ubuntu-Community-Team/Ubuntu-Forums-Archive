---
title: "Installing Wine problems."
date: 2006-02-04
forum: Gaming &amp; Leisure
---

### Post by lgmdaniel on 2006-02-04
I've tried to install wine but I get the following errors:
```

niel@grinch:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  wine
0 upgraded, 1 newly installed, 0 to remove and 4 not upgraded.
Need to get 14.0MB of archives.
After unpacking 56.0MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  wine
Install these packages without verification [y/N]? y
Err http://wine.sourceforge.net binary/ wine 0.9.6-winehq-1
  404 Not Found
Failed to fetch http://wine.sourceforge.net/apt/binary/wine_0.9.6-winehq-1_i386.deb  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

It appears to be calling the wrong file.. namely 0.9.6 and the current is 0.9.7 how would I resolve this?

---

### Post by lgmdaniel on 2006-02-04
Fixed it.. appears the [COLOR="Blue"]Packages.gz[/COLOR] in the [COLOR="SeaGreen"]http://wine.sourceforge.net/apt/binary/[/COLOR] folder links to the 0.9.6 source files but are 0.9.7. the [COLOR="Blue"]Packages.gz[/COLOR] files in [COLOR="SeaGreen"]http://wine.sourceforge.net/apt/breezy[/COLOR] are correct.
So I ran sudo [COLOR="Blue"]gedit /etc/apt/sources.list[/COLOR]
and changed the 
[COLOR="Blue"]deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/[/COLOR] 
to 
[COLOR="Blue"]deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) breezy/[/COLOR]

you may also need to run s[COLOR="Blue"]udo apt-get update[/COLOR] to pick up the new sources

---

### Post by obx-jdt on 2006-02-09
cool, but wouldn't it have been easier to open synaptic, search for wine, install it, then update it????  :-k

---

### Post by lgmdaniel on 2006-02-09
[QUOTE=obx-jdt]cool, but wouldn't it have been easier to open synaptic, search for wine, install it, then update it????  :-k[/QUOTE]

but the problem would have been the same.... just in a GUI... I'm a command line kind of guy.

---

### Post by obx-jdt on 2006-02-09
[QUOTE=lgmdaniel]but the problem would have been the same.... just in a GUI... I'm a command line kind of guy.[/QUOTE]
never the less, you have it working now 8-)
I like the command line too, but some things are faster useing synaptic.

---

### Post by lgmdaniel on 2006-02-09
[QUOTE=obx-jdt]never the less, you have it working now 8-)
I like the command line too, but some things are faster useing synaptic.[/QUOTE]

true.. but I've been working with UNIX for ten years now and I'm kind of set in my ways. Though I have been using DOS and windows longer... so I'm a bit flexible...

---

### Post by obx-jdt on 2006-02-10
[QUOTE=lgmdaniel]true.. but I've been working with UNIX for ten years now and I'm kind of set in my ways. Though I have been using DOS and windows longer... so I'm a bit flexible...[/QUOTE]
I've never use a true Unix system. Been useing Linux for about 2 years, so needless to say I still have alot to learn :rolleyes: Started with Mandrake.

---

### Post by lgmdaniel on 2006-02-10
[QUOTE=obx-jdt]I've never use a true Unix system. Been useing Linux for about 2 years, so needless to say I still have alot to learn :rolleyes: Started with Mandrake.[/QUOTE]
 There are lots of similarities, depending on what version of UNIX you've been using. But even those are different to each other. The main common parts are the oldests. Vi... ls... metacharaters. Stuff like that.

---

