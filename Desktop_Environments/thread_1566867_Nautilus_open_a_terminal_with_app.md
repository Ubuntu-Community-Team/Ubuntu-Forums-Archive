---
title: "Nautilus open a terminal with app"
date: 2010-09-02
forum: Desktop Environments
---

### Post by X5-655 on 2010-09-02
I have some adlib music files I want to be able to double click from Nautilus..  the command line program that will play them is adplay..  However, if I just do that, then when I double click, the music plays, but no way to stop it!

I tried "gnome-terminal adplay --output=oss" as the custom command but it doesn't seem to work..  I need it to open the terminal with adplay so i can stop the music when im done, since there's no GUI front end for this program..

ALSA is the default for this app, but it skips horribly, and OSS was the only output device that works..

---

### Post by X5-655 on 2010-09-03
Oh come on someone MUST know this..

---

### Post by mc4man on 2010-09-03
gnome-terminal -x adplay --output=oss

If you want to give it a custom name (probably would show up as "gnome-terminal"). then go to ~/.local/share/applications
Open up the userapp-gnome-terminal-XXXXXX.desktop in gedit and change the display name to whatever you wish (Name=

You may have more than one userapp-gnome-terminal-XXXXXX.desktop - delete the unneeded one(s)

---

### Post by X5-655 on 2010-09-03
It didn't work..  A terminal window appears then immediately dissapears..

---

### Post by mc4man on 2010-09-03
That generally works for me (mainly use to create several different mplayers.
Other way I sometimes use is to create a simple script and put in path
~/bin is where these things go here.

mkdir ~/bin and reboot

Ex. - I need an mplayer for some avi's that uses xv instead of the default vdpau
So  an executable  script in ~/bin named mplayervx, then first time from right click - use custom command I just insert mplayerxv, after that it's a choice
```
#!/bin/bash
gnome-terminal -x mplayer -vo xv "$1"
```

(or try adding "$1" to your command
(don't have any adplay (adlib ) tracks to see

---

