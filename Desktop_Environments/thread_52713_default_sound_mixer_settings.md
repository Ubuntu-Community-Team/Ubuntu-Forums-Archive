---
title: "default sound mixer settings"
date: 2005-07-28
forum: Desktop Environments
---

### Post by Copter on 2005-07-28
hi!

i have sound mixer aplet on my desktop panel (KDE). every time i start linux mixer values are messed up (some of them). does anyone know where can i set sound mixer default values?

thanks!

copter :]

---

### Post by Copter on 2005-07-30
guys, it has got to be possible :)

BUMP

---

### Post by heimo on 2005-07-30
[http://ubuntuforums.org/showthread.php?t=8959](http://ubuntuforums.org/showthread.php?t=8959)

Are you using Alsa? Try 
 ```
 sudo alsactl store
```

---

### Post by Copter on 2005-07-30
thanks for reply but it didnt work here :(  it saves some settings to asound.state file but they are nor reloaded on kde login. ive deleted asound.state file. after sudo alsactl store command the file was crated again but it still contained strange (for me) values. please see attachment.

copter :]

EDIT: if that is important i have 2 soundcards: ATI IXP (onboard), SB Audigy (pci). i changed the Audigy settings also using alsamixer -c1, than saved store command you wrote. it did not worked either...

---

### Post by Copter on 2005-07-30
ok, i did it :)

what exacly i did:

set mixer settings as i want them to be
```
alsamixer -c1
``` 
-c1 because i use my 2nd soundcard as default. after that i saved my settings
```
sudo alsactl store
``` 
after that i created KDE autostart script
```
nano ~/.kde/Autostart/mysound.sh
``` 
and wrote there
```
alsactl restore
```
than changed file access permission (i think it would work without that step)
```
chmod 755 ~/.kde/Autostart/mysound.sh
```
now everytime KDE starts it loads stored mixer settings :D

copter :]

---

### Post by heimo on 2005-07-30
Hey, great! And thanks for writing the solution, these forums are used by many, many users, and these posts are very useful.

---

### Post by Copter on 2005-07-31
this method works only on KDE restart through logout / login. after shutdown or reboot mixer is messed up again :(  dont know why it happens this way...

copter :]

---

### Post by heimo on 2005-07-31
Maybe you need that alsamixer -c1 line in beginning of that mysound.sh? 

EDIT: Oh, wait. That's not probably it. I don't know. Is it possible for you to disable the first (integrated?) sound card? In BIOS settings?

---

### Post by cutOff on 2005-08-01
[QUOTE=heimo]EDIT: Oh, wait. That's not probably it. I don't know. Is it possible for you to disable the first (integrated?) sound card? In BIOS settings?[/QUOTE]
Or maybe entering module's name into /etc/hotplug/blacklist.

---

### Post by Copter on 2005-08-03
[QUOTE=heimo]Maybe you need that alsamixer -c1 line in beginning of that mysound.sh? 

EDIT: Oh, wait. That's not probably it. I don't know. Is it possible for you to disable the first (integrated?) sound card? In BIOS settings?[/QUOTE]putting alsamixer -c1  pop ups mixer and i have to quit it manually. about second sound card - im using both sometimes (rare) so i would like to avoid disabling integrated one. but i will try that.

[QUOTE=cutOff]Or maybe entering module's name into /etc/hotplug/blacklist.[/QUOTE]em.. dont know exacly how it works  :neutral: when running alsamixer -c1 i see chip name (TriTech TR28602) but cant say what is the driver name for my Audigy.

solved :D

[HOWTO: Solve default sound mixer settings problems](http://ubuntuforums.org/showthread.php?p=292006)

---

