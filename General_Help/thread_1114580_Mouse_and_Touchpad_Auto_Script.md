---
title: "Mouse and Touchpad Auto Script?"
date: 2009-04-02
forum: General Help
---

### Post by bf109 on 2009-04-02
I am running Ubuntu 8.10 on a Vaio TZ. I use a USB mouse and many times per day I detach the mouse and use the touchpad. I was wondering if there is a way to auto detect the USB mouse detachment and have the mouse acceleration setting reduce speed? Could a script be written for something like that?

---

### Post by eldragon on 2009-04-02
yes, it can be done...

but first you have to enable SHMConfig on xorg.

if you got hotplugging enabled, this includes adding a fdi file for your touchpad. otherwise, just edit /etc/X11/xorg.conf and add 
```

option SHMConfig "on"

```

where it should apply (i think its server options)


once you got shmconfig enabled, you have to set some udev rules to be executed when the mouse is plugged or unplugged.


for this, create as root, the file /etc/udev/rules.d/01-touchpad.rules

and add these lines:
```

ACTION=="add", SUBSYSTEM=="input", RUN+="/usr/bin/synclient TouchpadOff=1"
ACTION=="remove", SUBSYSTEM=="input", RUN+="/usr/bin/synclient TouchpadOff=0"

```

restart X and you will have the desired effect.

under xserver 1.6 this does not work, there is a problem with synclient being run by udev for some reason, couldnt get it to work yet :(

---

### Post by bf109 on 2009-04-03
Thanks eldragon. You are talking to a total newb here so it looks like I will have quite a lot to read about to get this working. :-) Thanks for the information.

---

### Post by eldragon on 2009-04-03
> **bf109 said:**
> Thanks eldragon. You are talking to a total newb here so it looks like I will have quite a lot to read about to get this working. :-) Thanks for the information.

no offense, but ive given up on the whole step by step kind of solutions, cause if something goes wrong, its much more difficult to fix if the one behind the keyboard does not know what he's doing. but instead of leaving you with nothing, ive decided to give some pointers... the hard part is all spelled out for you, you just need to decypher how to get shmconfig working (which is the part that could leave you with no mouse support).

anyway, if you have xorg 1.4 or older, edit xorg.conf

if you have xorg 1.5 or later, create a fdi file. many info on how to do that on the web.

---

### Post by bf109 on 2009-04-03
> **eldragon said:**
> no offense, but ive given up on the whole step by step kind of solutions, cause if something goes wrong, its much more difficult to fix if the one behind the keyboard does not know what he's doing. but instead of leaving you with nothing, ive decided to give some pointers... the hard part is all spelled out for you, you just need to decypher how to get shmconfig working (which is the part that could leave you with no mouse support).

anyway, if you have xorg 1.4 or older, edit xorg.conf

if you have xorg 1.5 or later, create a fdi file. many info on how to do that on the web.

No, no, I totally understand. Thanks again for the information. I'm sure that I am on the right track now.

---

