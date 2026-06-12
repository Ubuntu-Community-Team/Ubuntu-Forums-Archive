---
title: "Default soundcard resets after every boot"
date: 2006-07-02
forum: Desktop Environments
---

### Post by xerosis on 2006-07-02
Every time I reboot, my default soundcard in the ubuntu sound section in 'preferences' changes from my external soundcard to my onboard. It's pretty annoying to have to change it everytime I reboot, is it hardcoded anywhere that I need to change it or something?

---

### Post by xerosis on 2006-07-02
shameless bump, I imagine this is an easy problem to solve?

---

### Post by elv on 2006-10-27
This seems to be a rather anoying bug un Edgy,
I also have this problem.Dose anyone know how to fix this




00 and  bump I guess:D

---

### Post by weissnich on 2006-10-30
Same problem here,
this is really annoying](*,) 

Solutions?

---

### Post by Eremit on 2006-10-30
/etc/modprobe.d/sound
solves your problem I guess

mine looks like this:
```
options snd_ens1371 index=0
options snd_via82xx index=1
```
```
cat /proc/asound/modules
```
tells you your cards

---

### Post by weissnich on 2006-10-30
There is no
/etc/modprobe.d/sound
in Edge.
I tried to switch numbers in alsa-base
install sound-slot-0 /sbin/modprobe snd-card-1
install sound-slot-1 /sbin/modprobe snd-card-0
but that doesn't work.

---

### Post by weissnich on 2006-10-30
Has someone a workaround for this problem?

Thanks!

---

### Post by Eremit on 2006-10-30
> **weissnich said:**
> There is no
/etc/modprobe.d/sound
in Edge.

Than create it :)

---

### Post by timbonz on 2006-10-30
I had the same problem with onboard sound and my SB-Live card.  Not on my Ubunutu box at the moment but from memory the file to alter is "/etc/modules/alsa-base"  and at the end put;

options snd_???? index=0
options snd_???? index=1

Where ???? is the card name you want first then it should work OK after a reboot or a "/etc/init.d/alsa-base restart"

Regards
Tim
:cool:

---

### Post by ubman on 2006-10-30
> **weissnich said:**
> Has someone a workaround for this problem?

Thanks!

Mine i just disabled it in my bios!:)

---

### Post by weissnich on 2006-10-30
In Gnome sometimes the standard sound card is my first sound card and sometimes my second and I can't disable it in the BIOS settings, because I use it in Windows.
Maybe I can blacklist the second sound card?

---

### Post by timbonz on 2006-11-01
Had already checked that and yep it is disabeled... ubuntu being too fancy?

Tim
:cool:

---

### Post by The Keeper on 2006-11-02
There is a bug in launchpad about this.
[https://launchpad.net/distros/ubuntu/+bug/66210](https://launchpad.net/distros/ubuntu/+bug/66210)

It has not gotten much attention from devs though.

---

