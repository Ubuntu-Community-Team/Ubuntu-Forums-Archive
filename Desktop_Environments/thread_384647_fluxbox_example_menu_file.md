---
title: "fluxbox example menu file"
date: 2007-03-14
forum: Desktop Environments
---

### Post by mozkaynak on 2007-03-14
Could someone share the menu configuration file.
I am so new to fluxbox and I want to start someone else's document as a start point.

I want to be able to run terminal, browser and open office and administration tools with right click.

Thanks....

Edit: I use ubuntu 6.10 (gnome)

---

### Post by yabbadabbadont on 2007-03-14
Please search before posting.  :D

[http://www.ubuntuforums.org/showthread.php?t=371144&highlight=fluxbox+howto](http://www.ubuntuforums.org/showthread.php?t=371144&highlight=fluxbox+howto)

---

### Post by yabbadabbadont on 2007-03-14
Here is a simple example too:

[http://www.ubuntuforums.org/showpost.php?p=1886994&postcount=137](http://www.ubuntuforums.org/showpost.php?p=1886994&postcount=137)

---

### Post by kerry_s on 2007-03-14
Here's what i'm using now, just change to your needs->

```
[begin] (Fluxbox)

[exec] (Files) {exec emelfm} 

[submenu] (Net)
 [exec] (Firefox) {exec firefox}
 [exec] (Gaim) {exec gaim}
 [exec] (Prozilla) {exec xterm -T "Prozilla" -e dproz}
[end]

[submenu] (Sound)
 [exec] (VLC) {exec vlc}
 [exec] (Volume) {exec xterm -e alsamixer}
[end]

[submenu] (Admin)
 [exec] (Synaptic) {exec gksu synaptic}
 [exec] (Root-Files) {exec gksu emelfm}
 [exec] (Root-run) {exec gksu}
 [exec] (Printer) {exec system-config-printer}
[end]

[submenu] (Settings)
  [restart] (Restart)
  [config] (Configuration)
   [submenu] (Styles)
      [stylesdir] (/usr/share/fluxbox/styles)
      [stylesdir] (~/.fluxbox/styles)
   [end]
 [submenu] (Backgrounds)
  [exec] (Black) {exec fbsetroot -solid black}
  [wallpapers] (/usr/share/fluxbox/backgrounds)
  [wallpapers] (~/.fluxbox/backgrounds)
 [end]
[end]

[separator]
[exec] (Run Program) {exec fbrun -w 600 -h 50 -nearmouse -font Sans-16}

[submenu] (ScreenShots)
 [exec] (Snap) {exec scrot %T.jpg}
 [exec] (Select) {exec scrot -s -b %T.jpg}
 [exec] (Wait 5) {exec scrot -d 5 %T.jpg}
[end]

[separator]
[submenu] (Debian-menu)
 [exec] (Update-menus) {exec update-menus}
 [include] (~/.fluxbox/fluxbox-menu)
 [exec] (About) {(fluxbox -v; fluxbox -info | sed 1d) 2> /dev/null | xmessage -file - -center}
[end]


[separator]
[exec] (Screen Off) {exec /home/user/.screen-off}

[submenu] (Logout)
 [exit] (Exit)
 [exec] (Reboot) {exec sudo /sbin/reboot}
 [exec] (Shutdown) {exec sudo /sbin/shutdown}
[end]


```

---

