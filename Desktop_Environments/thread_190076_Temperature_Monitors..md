---
title: "Temperature Monitors."
date: 2006-06-05
forum: Desktop Environments
---

### Post by chazzy on 2006-06-05
Hi all,

I have a P4 3Ghz box which reports the temps in the bios/windows fine, but under linux "Computer Temperature Monitor" tells me I have no sensors ...

Should I murder myself now, or does anybody have a suggestion on what direction to look?

Thanks in advance!

Chaz

---

### Post by Flyn on 2006-06-06
You need to get lmsensors from the repos, try running a search for it in the forums and maybe google.

---

### Post by chazzy on 2006-06-06
Ah smashing, works a treat!

Thanks :)

---

### Post by Flyn on 2006-06-06
Most welcome :)

---

### Post by ponkan on 2006-06-26
I've got the same problem, can't find the sensors. sudo apt-get install lm-sensors; sudo modprobe i2c-dev;sudo sensors-detect and I get "No i2c devices found. Use prog/mkdev/mkdev.sh to create them"
Now, so I use the script, and it works and now I have sensors. Funny thing is, I'm supposed to have a dynamic dev; a cat of /proc/mounts gives "udev /dev tmpfs rw 0 0"

I suppose I can put mkdev.sh into my /etc/rc.local, but I'd rather do something to resolve the lack of automatic node creation. How do I do this?

---

### Post by ponkan on 2006-06-27
I forgot to say, I'm running from a clean install of Xubuntu 6.06

---

