---
title: "Opera Fonts - Feisty &amp; Opera 9.20"
date: 2007-04-18
forum: Desktop Effects &amp; Customization
---

### Post by UrbanSlayer on 2007-04-18
I have a bit of a problem with Opera and the rendering of its fonts.  Not just on webpages, but its menu's etc as well.

They look like this - [http://eclair.kiddygrade.org/Images/opera.png](http://eclair.kiddygrade.org/Images/opera.png)

I am using the deb from [www.opera.com](www.opera.com) for Edgy as there does not appear to be a Feisty build yet.  I am running in KDE currently (although the font issue also occurs in Gnome).

I have tried adding - 
export QT_XFT = true to /usr/bin/opera
and have tried adding - 
Enable Core X Fonts=0 to /etc/operarc6 
but with no effect.  Can anyone help?  I much prefer Opera to Firefox and want to keep using it, but this font issue is bugging me.

Thanks!

---

### Post by kpel on 2007-04-18
I'm running Feisty with Opera 9.20 as well, using the Edgy build.  Installing the Microsoft Core Fonts from Add/Remove Programs helped a great deal for me (I just did this today, actually).  It appears that when I installed the MS Core Fonts Opera automagically picked them out and started using them.

The only issue now is that things are smaller.  Not a big deal since I can simply use the beautiful zoom feature in Opera, though I'll eventually go into Tools>Preferences>Advanced Tab>Fonts and set everything correctly.  It also appears that a few things are still using the ***-ugly fonts and I'll need to update those as well, though most pages display with the new ones.

---

### Post by UrbanSlayer on 2007-04-19
I have got the MS fonts installed as well, and Opera did pick them up straight away when they got installed.  That screenshot is from Opera using the MS fonts, it looked worse before they were installed.

---

### Post by kpel on 2007-04-19
Don't know if I can be of much more help then.  Everything seems to have straightened itself out for me, though I would suggest double-checking the entire font listing to make sure that Opera is set to use them all.  My listings  all have either [monotype] or [microsoft] after them.  The only one I had to change by hand was the monospace font in the web pages tab as it was set to a very faint version of Arial.


The thing is that the forum home page looked **exactly** the same for me before I installed the MS fonts, so I'm convinced that something either broke during the install or Opera simply isn't using them (at least not for everything).

---

### Post by desperado666 on 2007-04-19
[http://wiki.ubuntuusers.de/Opera/Optik](http://wiki.ubuntuusers.de/Opera/Optik)

---

### Post by UrbanSlayer on 2007-04-19
Thanks, that seems to have done the trick!  Took me a while to translate, but all good.  Cheers!

---

### Post by paradoxni on 2007-04-20
ubuntuusers.de seems to be down, any chance of someone posting a step by step ?

---

### Post by paradoxni on 2007-04-20
ive used qtconfig and polymer-config to change QT3 look and style, but it wont work in opera? just get the same ugly menus :(

---

### Post by Colonel Kilkenny on 2007-04-21
> **paradoxni said:**
> ive used qtconfig and polymer-config to change QT3 look and style, but it wont work in opera? just get the same ugly menus :(

Are you using shared version of Opera instead of static one?
Only shared version can use qt-styles.

Though, there is some sort of problem with feisty & opera 9.20. I have the same problem with shared-version as well. Usually I don't have any menus visible (alt+f11) so that doesn't bother me much, but it would be nice to get it working.

---

### Post by kpel on 2007-04-22
Since my last post in this thread I managed to pretty much hose my Ubuntu install.  Since I wanted to move which drive it was on anyway I did a reinstall (using the same disc).  The first two things I did, in order, was to install the nvidia-glx-new drivers and then Opera....and now for some reason the fonts are fine without any messing around.  I used the same Opera .deb (Edgy) and didn't install any font packages.

I still can't figure out what changed.  *shrug*

---

### Post by paradoxni on 2007-04-22
Just tried removing opera / installing nvidia-glx-new / reinstalling opera from edgy dep, but still the same.

It did manage to break my X server thou but a quick reconfigure seemed to sort it again.

The opera problem probably has something to do with the fact im in 64bit Ubuntu and did a forced architecture install of 32bit Opera?

---

### Post by t_anjan on 2007-04-23
I'm on Opera 9.2 on Feisty 64bit too. And I'm also having the same problem. All the remaining applications are OK. It's only Opera that downright hurts the eyes. 

It used to look OK (not as good as Firefox, though) before I installed updated font packages mentioned on this thread: [http://ubuntuforums.org/showthread.php?t=343670](http://ubuntuforums.org/showthread.php?t=343670)

After the update, the rest of Ubuntu looked a LOT better, but Opera took a nosedive. I've used the same font update packages on Edgy, with Opera 9.2 and there is no such problem there.

I hope UrbanSlayer posts what he found useful on that Ubuntu Users wiki as it is not accessible now.

---

