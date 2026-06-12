---
title: "beryl  uninstall"
date: 2007-02-18
forum: Desktop Environments
---

### Post by seanmbarrett on 2007-02-18
hi installed beryl and i twas working. then i rebooted my comp and ubuntu starts to boot then a blank screen. i get get i nto the root menu from safe mode.. is there anyway to delete beryl from there so i can get back into ubuntu start up screen. i think i am way over my head on this. thanks for the help. oh yeah used wiki to install
sean

---

### Post by Old Pink on 2007-02-18
Get as far as you possibly can, and then hold ctrl and alt and tap F1. Then log in to the terminal and type ```
sudo aptitude remove beryl
```(and anything related to it) and then use ```
sudo reboot now
``` to reboot. 

This "safe mode" you speak of, if it allows you to access terminal, just use the two commands above in order and you should be back to normal in no time. :)

---

### Post by jvc26 on 2007-02-18
I think the full uninstall (removing config files too) would be:
```

sudo apt-get --purge remove beryl emerald-themes

```
Il

(P.s. it may be -purge rather than --purge I havent used it in a while)

---

### Post by seanmbarrett on 2007-02-18
well i tried both in recovery mode and it will still not start up when rebooted. any ideas thanks
sean

---

### Post by seanmbarrett on 2007-02-18
well i will just reinstall that wil work. thanks sean

---

### Post by Yellowbelly on 2007-02-26
I have the same problem actually and thought of the same way to fix it. I don't think removing beryl is going to do it. Probably going to have to set metacity as the default window manager before ubuntu starts again although I don't know how to do that through the terminal. Would anyone know how to do this?

---

### Post by seanmbarrett on 2007-02-26
i ended up reformatting and reinstalling ubuntu. saved me some grief. sean

---

### Post by eggdeng on 2007-02-26
The bone in the throat here is the beryl (& emerald) startup command(s). If you created them in the startup programs dialog box, they are represented by files in the directory /home/username/.config/autostart.

Type
```

ls /home/username/.config/autostart

```
to see what files you have
then
```

sudo rm /home/username/.config/autostart/filename

```
to delete unwanted files & reboot.

---

### Post by saeid on 2007-03-03
Thanks **Old Pink**

---

### Post by shareMenaPeace on 2007-03-03
See my signature for a complete beryl uninstall way.

---

### Post by igknighted on 2007-03-03
> **Illuvator said:**
> I think the full uninstall (removing config files too) would be:
```

sudo apt-get --purge remove beryl emerald-themes

```
Il

(P.s. it may be -purge rather than --purge I havent used it in a while)

it is --purge.  Any time you use a word (like --help or --purge you need to dashes to tell the computer the connected letters are a word.  -purge is the same as -p -u -r -g -e, each letter taken as an individual command.

---

