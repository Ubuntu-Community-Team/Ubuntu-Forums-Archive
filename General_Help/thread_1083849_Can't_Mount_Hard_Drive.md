---
title: "Can't Mount Hard Drive"
date: 2009-03-01
forum: General Help
---

### Post by tom_the_drummer on 2009-03-01
Hi guys - it's been a while!

Basically a friend has given me her laptop to fix. I ran Knoppix off the live CD but didn't get on with it well so switched to Ubuntu. Just after it had loaded the computer shut down due to getting too hot. Before rebooting I switched again to Xubuntu - as it's faster - but now when I try and go onto the hard drive to get the data off it, Xubuntu says

"Can't mount drive. Can't find mount point".

Is there ANY way I can mount this drive as I REALLY need to get the data off it?


Cheers guys!


Tom

---

### Post by taurus on 2009-03-01
Open a terminal and post the output of these commands here.

```
sudo fdisk -l
df -h
```
You probably have to mount it by hand from a terminal first before you can access it.

---

### Post by tom_the_drummer on 2009-03-01
The first one gives me a load of commands to chose from and also at the top says -1 is an invalid option.

The second gives me loads of info on the filesystem.

How do I mount it by hand?

---

### Post by vanadium on 2009-03-01
[quote=taurus]
Open a terminal and post the output of these commands here.

sudo fdisk -l
df -h

[/quote]

...unless you do not care for help

---

### Post by taurus on 2009-03-01
That should be a lower case letter L, not number 1.  Again, run each command from a terminal and post the output here.

```
sudo fdisk -**[COLOR="Blue"]l[/COLOR]**
df -h
```

---

### Post by tom_the_drummer on 2009-03-01
Cheers guys but got it sorted now!

Just rebooted with Knoppix, which saw the drive straight away, back into Xubuntu and all is well!

---

### Post by mistypotato on 2009-03-01
taurus,

I couldn't help but notice your avatar and the caption.

Would you mind telling me what that little key (with legs no less) is
running from :P

---

### Post by taurus on 2009-03-01
> **mistypotato said:**
> taurus,

I couldn't help but notice your avatar and the caption.

Would you mind telling me what that little key (with legs no less) is
running from :P

That is the ESC key.  You couldn't read it clearly because I have to compress it to reduce it due to size limitation for avatar.

---

### Post by mistypotato on 2009-03-06
The "ESCAPE" key......

:lolflag:

---

