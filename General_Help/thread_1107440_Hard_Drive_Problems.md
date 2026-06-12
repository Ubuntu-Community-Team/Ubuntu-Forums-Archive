---
title: "Hard Drive Problems"
date: 2009-03-26
forum: General Help
---

### Post by McTricks on 2009-03-26
Ok, so, with the suckiness of windows, I'm getting a BSOD everytime I start up windows (XP, for the record)... and I need to get my info off off of my Windows Hard Drive... so I booted up Ubuntu intending to open it up through there and get everything off...

But when I try to mount it, I get a "Cannot Mount Volume Error"

I've encountered this error before, and it's when I don't safely remove my external HD from windows... But I can't really boot up windows to shut it down, now can I?

I NEED to get my files... is there any way I can?

---

### Post by ooburns on 2009-03-26
Can you start Windows in safe mode? (Hit F8 after selecting Windows from the boot menu).  If you can, then you can shut it down cleanly.

---

### Post by McTricks on 2009-03-26
I'll try that...

---

### Post by McTricks on 2009-03-26
No, that dosn't work... same blue screen :(

---

### Post by Ptero-4 on 2009-03-26
type into the terminal:
```
sudo mount -t ntfs -o force /dev/*windows partition* /media/windows
```
You'll need to put the partition number instead of *windows partition*, and you'll need to create the "windows" folder inside /media before trying to mount the partition.
You can use gparted to see where is your windows partition.

---

### Post by McTricks on 2009-03-26
Thanks anyways, but I've just got it... I did this:

```
sudo apt-get ntfsprogs
sudo ntfsfix /dev/sda1
```

---

