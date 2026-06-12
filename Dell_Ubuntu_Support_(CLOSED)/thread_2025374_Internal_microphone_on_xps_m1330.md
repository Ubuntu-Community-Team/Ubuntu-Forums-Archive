---
title: "Internal microphone on xps m1330"
date: 2012-07-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by newcolour78 on 2012-07-14
Hi all,
  I have just upgraded from 10.04LTS to 12.04LTS. Upon upgrade, the internal microphone stopped working. It was working fine before the upgrade. The external mic (front plug) does not work either. Very uncool.

I have tried installing and playing with pavucontrol and alsamixer to no good :(

Any advice is welcome.

>> uname -a
Linux Simone-Dell 3.2.0-26-generic-pae #41-Ubuntu SMP Thu Jun 14 16:45:14 UTC 2012 i686 i686 i386 GNU/Linux

---

### Post by newcolour78 on 2012-07-15
Bump! 

This is very important and it is such a weird regression!

Cheers,
S.

---

### Post by oliwek on 2012-11-20
Sorry, this is a late reply, but you should control the volume in gnome-volume-control (front Line in is muted by default)

source : [http://web.archive.org/web/20080226122653/http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Second_Headphone_Jack_Does_Not_Work](http://web.archive.org/web/20080226122653/http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Second_Headphone_Jack_Does_Not_Work)


[I][COLOR="Sienna"]1. Open the GNOME volume control tool:

$ gnome-volume-control
Select Edit -> Preferences and verify the following tracks are visible: Surround, Front and Line In as Output. Click Close when done.

2. In the Switches tab, place a checkmark by Line In as Output by clicking on the square next to it. This unmutes the second headphone jack.

3. In the Playback tab, you can control the volume or mute the laptop speakers with Front. You can control the volume (or mute) the headphones volume with Surround.

Retrieved from "http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Second_Headphone_Jack_Does_Not_Work"[/COLOR][/I]

---

