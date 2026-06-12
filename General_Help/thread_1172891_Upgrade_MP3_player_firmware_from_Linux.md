---
title: "Upgrade MP3 player firmware from Linux"
date: 2009-05-29
forum: General Help
---

### Post by blackSP on 2009-05-29
In my attempt to completely discard Windows I need to be able to upgrade the firmware from devices that connect through USB like MP3 player, GPS.

Has anybody figured this out? The search function doesn't reveal a whole lot in this field.

I run an firmware installer for my Sony MP3 player with Wine but that didn't do anything, couldn't find the device.

If you can point me in the right direction?

---

### Post by Soul-Sing on 2009-05-29
For GPS firmware it is still difficult in the Netherlands, some ubuntu users do run in virtualbox/vmware microsoft windows to get
the job done.

---

### Post by blackSP on 2009-05-29
Hi. Why is it difficult in the Netherlands? I just want to be able to upgrade any USB device (with English (language) firmware).
Thanks!

---

### Post by Soul-Sing on 2009-05-29
> **blackSP said:**
> Hi. Why is it difficult in the Netherlands? I just want to be able to upgrade any USB device (with English (language) firmware).
Thanks!

I mentioned that above because i know these issues, because i live in the Netherlands, and i'am active on Dutch ubuntu forum. :)
I know members only using virtualbox/windows for their GPS software/firmware.....

---

### Post by blackSP on 2009-05-29
OK. So if I understand correctly you can do this type of upgrade from inside Virtualbox running Windows? That would be 'good' news but still requires Windows to be installed.

Any other options?

---

### Post by Chronon on 2009-05-29
I don't think you can expect a one-size-fits-all answer here.  Different devices store firmware in different locations that may be more or less accessible.  Unless the device offers a native linux firmware upgrade method then it seems you will have to resort to running a windows upgrader from a VM (as suggested already) or else figure out details about what the installer actually does and do that yourself through linux.

Quite a few MP3 players have on-board firmware upgrade capabilities such that if you load a new firmware file to the correct location on the player's disk and reboot, it will upgrade to the new firmware version.  Sometimes it's just a matter of overwriting the old firmware on disk with a new copy.  Other times there may be a recovery mode that allows you to restore a corrupted firmware.  This may also provide a method of installing a new firmware.  There are other options too (e.g. dd), but it's probably not too useful to discuss hypotheticals here.

I would check user forums for the devices I own for what the Linux users there are doing.  I.e., since it's so device specific you're probably better off sifting the subset of device owners who use Linux than Ubuntu users who use your device(s).

---

### Post by blackSP on 2009-05-29
You're probably right. I'm looking at a Garmin Mapsource and Sony HDxxxx updater, which are executables that access the device through the USB port. Wine is no go, I'll try the VM ware type approach. It does piss me off however that I'm still going the be dependent om Mircosfot. I really can't stand that...

---

### Post by Chronon on 2009-05-29
Like I said, it may be that other Linux users have figured out how to update the firmware on these devices already.  It's worth checking into, at least.  I have found Linux users to be a resourceful bunch.  ;)

---

### Post by blackSP on 2009-05-30
Let's hope they all find this thread and respond with good news :popcorn:

---

### Post by cubeist on 2009-05-30
you might have luck with a linux based firmware...if your device is compatible...

[http://www.rockbox.org/](http://www.rockbox.org/)

ps, in regards to your sig, ATI cards work fine in Jaunty with the latest 9.5 driver...

update2, sorry, just noticed there is no port of rockbox for sony players...

---

### Post by Chronon on 2009-06-01
Just to clarify, Rockbox is a firmware for digital audio players (DAPs).  It is not actually based on Linux, though I'm not sure why this matters either way. A Rockboxed DAP just behaves like a UMS device.

Rockbox has not been ported to either device mentioned in this topic.

---

### Post by blackSP on 2009-06-02
Sig updated, I've been running with 9.5 without any further problems.Even Compiz is now fine :)

---

### Post by blackSP on 2009-06-02
Very cool stuff but too bad, not for Sony players. I may just try to find an iriver or sansa, just to play with this. Looks cool!

---

