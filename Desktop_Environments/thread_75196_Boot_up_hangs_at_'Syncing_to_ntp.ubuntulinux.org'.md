---
title: "Boot up hangs at 'Syncing to ntp.ubuntulinux.org'"
date: 2005-10-13
forum: Desktop Environments
---

### Post by XtremeGamer99 on 2005-10-13
Can't rememeber the exact way it says it, but my Ubuntu hangs there while booting, and then goes to a black screen with all the steps, and freezes. How can I fix this?

Thanks.

---

### Post by magomago on 2005-10-13
my guess is because the site is being hammered

---

### Post by XtremeGamer99 on 2005-10-13
Well, this is been happening for the past two days.

I'm on Ubuntu right now on my secondary drive, and when it boots up, it either says 'ok' or 'failed' and just keeps booting. My primary Ubuntu freezes.

I am able to edit files through my secondary Ubuntu, so if I need to edit something to fix this, I'm all for it.

---

### Post by drogoh on 2005-10-13
You can either disable this by:

'sudo rm /etc/rcS.d/S51nptdate'

or you can change the default behavior by editing /etc/defaults/ntpdate, commenting NTPSERVERS="ntp.ubuntulinux.org" out and uncommenting NTPSERVERS="pool.ntp.org"

---

### Post by bored2k on 2005-10-13
The easier way is to just do
```
sudo chmod -x /etc/init.d/ntpdate
```

---

### Post by XtremeGamer99 on 2005-10-13
[QUOTE=drogoh]or you can change the default behavior by editing /etc/defaults/ntpdate, commenting NTPSERVERS="ntp.ubuntulinux.org" out and uncommenting NTPSERVERS="pool.ntp.org"[/QUOTE]

Thanks, that worked.

I was thinking it was more serious than this, seeing as I was editing partitions before this happened. I'm just curious now - what could have caused it?

---

### Post by bored2k on 2005-10-13
I would think your internet is not fully activated at that step, making it retrying several times until it gives up.

---

### Post by XtremeGamer99 on 2005-10-13
That's what I thought at first, though my interent is always connected.

---

### Post by ssam on 2005-10-13
ctrl+c will make it give up waiting for the ntp server and skip to the next step. if you are usually plugged into the interent, but occationally you need to boot with out being plugged in this is a less invasive solution.

---

### Post by drogoh on 2005-10-13
I'm thinking maybe name resolution....

---

