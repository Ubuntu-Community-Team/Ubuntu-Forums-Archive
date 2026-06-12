---
title: "Dual boot issue - can't think of informative title"
date: 2009-05-13
forum: General Help
---

### Post by tjsilver on 2009-05-13
Hi all,

I have XP on my laptop and Ubuntu on an external USB HDD ( an old 3.5" IDE in a caddy - so it's a bit bulky and not exactly portable for everyday use).

When I attach the external drive and boot Ubuntu from a live CD 'something' happens and subsequently I can only boot into XP if the external drive is attached.

For various reasons, I need (would very much like) to be able to boot straight into XP - without the caddy being attached.

So, how do I access Ubuntu while retaining the ability to boot straight into XP - without the external drive being attached?

Am I asking for too much?

Tim

---

### Post by Legace on 2009-05-13
You've installed GRUB (the boot-loader, or the "thing" that loads your operating system) into the external drive. You'll need to install into the internal drive to make it work.. :)

(Can't help ya with that.. Someone wiser, and someone with more time could, though :))

---

### Post by pro003 on 2009-05-13
external drive has no significance if you have xp and ubuntu on 'internal' drive.

what you want is to boot straight into xp, if I understood you well?

then you;ll need to edit your boot conf file

backup first your original file:

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.BAK
```

and then edit:

```
sudo gedit /boot/grub/menu.lst
``` 

scroll down to Ubuntu 9.04 blah blah and right below that is your other operating system which is Windows XP - just copy the whole thing and place it in front of Ubuntu 9.04...
thats how you're gonna go straight to XP at boot... 

if that was not your question, am sorry then...

---

### Post by sir_nasty on 2009-05-13
Ubuntu is on the external hdd, xp is on internal so editing grub won't help....

try opening partition manager in ubuntu, set the xp hdd with the flag "boot"  (after testing remove the boot flag from ubuntu)

shut down the computer, disconnect the external drive, turn the computer on and if it works then you need to edit windows boot.ini to load the external drive.

---

