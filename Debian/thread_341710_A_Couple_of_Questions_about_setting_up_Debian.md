---
title: "A Couple of Questions about setting up Debian"
date: 2007-01-19
forum: Debian
---

### Post by happy-and-lost on 2007-01-19
I installed Debian Etch last night, and am absolutely amazed by the speed of it, I just need a few things to get it working...

1. This is basic Linux useage: how do I permanently mount a partition? I have a "Stuff" partition on sda3 which I'd really like to get into.

2. Iceweasel. Great, but the fonts render badly. Any way of getting the old fox back?

3. Tango. "non-free"', apparently, but it's refusing to compile (Says I need Icon-naming-utils which I have!

4. UK DVORAK keymap. Where do I find Ubuntu's UK DVORAK keymap and how would I add it to 
Debian (GNOME)?

5. Touchpad is tediously slow. Driver issue?

Cheers :)

PS. Anyone know any good repos for Etch? Stuff like msttcorefonts are missing.

---

### Post by kerry_s on 2007-01-19
Try looking through there forum for debian specific stuff-> [http://forums.debian.net/index.php?sid=ae1299730c7953920cb50864af27a4a6](http://forums.debian.net/index.php?sid=ae1299730c7953920cb50864af27a4a6)

I just wiped my sid install about a week ago, it is fast but somethings you really have to work at just to get it running right and that ice weasel was unstable as heck for me. Try qsynaptics for the touchpad, you'll have to google for the instructions i can't remember off the top of my head. I've seen answers to most of your questions in there forum when i was setting mine up. Have fun. :)

---

### Post by AgenT on 2007-01-21
> **happy-and-lost said:**
> I installed Debian Etch last night, and am absolutely amazed by the speed of it, I just need a few things to get it working...

1. This is basic Linux useage: how do I permanently mount a partition? I have a "Stuff" partition on sda3 which I'd really like to get into.

2. Iceweasel. Great, but the fonts render badly. Any way of getting the old fox back?

3. Tango. "non-free"', apparently, but it's refusing to compile (Says I need Icon-naming-utils which I have!

4. UK DVORAK keymap. Where do I find Ubuntu's UK DVORAK keymap and how would I add it to 
Debian (GNOME)?

5. Touchpad is tediously slow. Driver issue?

Cheers :)

PS. Anyone know any good repos for Etch? Stuff like msttcorefonts are missing.
It looks like you have misconfigured something, probably a repository because msttcorefonts is available in contrib:
[http://packages.debian.org/testing/x11/msttcorefonts](http://packages.debian.org/testing/x11/msttcorefonts)

Tango does not depend on that utility (although it may be packaged with Tango):
[http://packages.debian.org/testing/x11/tango-icon-theme](http://packages.debian.org/testing/x11/tango-icon-theme)

About locales: you must have chosen the wrong locale during install! Not to worry as you can change it. For changing locales, do:
```
sudo dpkg-reconfigure locales
```To always havea partition mounted you need to add a line in your /etc/fstab file (make sure to have it set as automount).

Touchpad being slow probably means you have to change a speed value either in xorg.conf or your desktop environment. xorg.conf is usually better because it is system wide and not desktop environment specific.

---

### Post by xabbott on 2007-01-21
> **happy-and-lost said:**
> I installed Debian Etch last night, and am absolutely amazed by the speed of it, I just need a few things to get it working...

1. This is basic Linux useage: how do I permanently mount a partition? I have a "Stuff" partition on sda3 which I'd really like to get into.

2. Iceweasel. Great, but the fonts render badly. Any way of getting the old fox back?

To fix this I ran 
```
dpkg-reconfigure fontconfig-config
```
I use an lcd monitor and I selected auto-hinter, subpixel rendering to: always, and no to bitmap fonts. Also make sure to get the microsoft fonts. If you still want Firefox you can just download it from [getfirefox.com]("http://getfirefox.com") or you can use [Swiftfox]("http://getswiftfox.com").

> **happy-and-lost said:**
> 
(/snip)
PS. Anyone know any good repos for Etch? Stuff like msttcorefonts are missing.
Only third party repo I ever needed in Etch was [debian-multimedia.org]("http://www.debian-multimedia.org/").

---

### Post by stream303 on 2007-01-22
It is Xabbot's information (and other contributors too!) about things like configuring fonts from the cli with dpkg-reconfigure fontconfig-config can really save your day.

Something common I found that can ease frustration when first installing Debian is to make sure the following is installed *before* installing base X packages if you are running into trouble:

mdetect
xresprobe
discover1 (or just discover - depending on situation)
hwinfo
laptop-detect

You can always install these after the fact, and run
dpkg-reconfigure xserver-xorg
to try and automatically fix some problems.

---

