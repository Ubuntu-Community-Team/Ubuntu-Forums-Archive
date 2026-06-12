---
title: "DOSbox keyboard layout problem"
date: 2005-07-26
forum: Gaming &amp; Leisure
---

### Post by blueturtl on 2005-07-26
Retrieved and installed DOSbox on Ubuntu through some new repositories and I can't get the thing to work. It boots ok, but my Finnish keyboard is giving me trouble I assume, as some characters don't print at all. This wouldn't be so critical if **:** wasn't one of the keys. I can't change the drive or do any mounting if this key doesn't work. I tried CTRL+F1 but the key isn't listed there for rebinding.  :-|

---

### Post by blueturtl on 2005-07-26
Circumventing the problem by using the codepage as my reference.
Hitting the ALT key and a number combination let's me use the keys that are inaccessible otherwise.

ALT+58 is :

I've actually managed to install and run Command & Conquer, although the game is way too laggy to be playable. Is there something I can do to speed things up or is this just matter of hardware?

---

### Post by SolidAndShade on 2005-07-27
To increase the emulator's CPU speed, use Ctrl-F12. Ctrl-F11 decreases the emulation speed. Ctrl-F8 and Ctrl-F7 increase and decrease the frameskip, which can also be useful for faster emulation.

SolidAndShade

---

### Post by blueturtl on 2005-08-18
Seems to be that DOSbox is built for American keyboards by default, that's why some keys don't seem to work. I found a partial work-around:

[http://projects.freedos.net/keyb/](http://projects.freedos.net/keyb/)

This utility will switch the keyboard layout with accordance to the KEYBOARD.SYS file, although I haven't gotten it to work perfectly, I'm now able to use the keys / and : as I should which makes using DOSbox just that much easier.

---

### Post by PtS on 2005-08-21
Where do i get the file keyboard.sys?
I ran "keyb.exe sw" in dosbox to find out i didn't have keyboard.sys...
I wouldn't be able to get this far without your "Alt+58" tips, and i hope you'll help me with this too. :)

---

### Post by blueturtl on 2005-09-05
keyboard.sys can be found in any DOS distribution. If you don't have some old MS-DOS install disks laying around (not that we'd want to touch them anyway  ;-)  ) you should download FREEDOS. FREEDOS aims at being a total MS-DOS replacement, and they should include a keyboard configuration file. You can propably unzip that file without having to install the distribution itself. Hope this helps.

---

### Post by Zleep-Dogg on 2009-05-05
well, although an old topic, I found it as first hit on a google search...

anyway, the solution is much more simple...

see
[http://www.dosbox.com/wiki/KEYB](http://www.dosbox.com/wiki/KEYB)

so to get danish layout, I type "KEYB dk"

the settings can also be loaded from a conf-file - unfortunately there is no "default" conf-file, so it must be specified from the command line - it could be done simply by specifying an alias (alias dosbox='dosbox -conf /path/to/configfile')

---

### Post by CharmyBee on 2009-05-07
You can also build from the DOSBox CVS which fixes this issue, or you could change the usescancodes setting.

---

### Post by blueturtl on 2009-07-18
When I posted this thread the 'keyb [country code]' command did not yet function in DOSBox (or at least it was not compiled into the version in the repositories).

Nowadays it is indeed much simpler and I've found that DOSBox will often detect the proper keyboard layout also.

If I could I'd mark this thread solved.

edit:

p.s. There is a section of the dosbox.conf file that is designated as autoexec.bat, by putting the command there it will be automatically run on every startup.

---

