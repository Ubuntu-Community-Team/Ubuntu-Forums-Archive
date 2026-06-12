---
title: "permanent modprobe changes or autoexec.bat equivalent"
date: 2009-04-28
forum: General Help
---

### Post by wawacito on 2009-04-28
Hello all,

I hope someone can help me.
I'd like to run the following commands automatically everytime I boot the computer:
```
sudo rmmod uvcvideo
sudo modprobe uvcvideo quirks=16
```

How do I do this?  Is there a way I can make modprobe always use "uvcvideo quirks=16" instead of what it normally does?

If I can't then - is there an equivalent to "autoexec.bat" where I can put those commands and they will automatically run on every boot?

---

### Post by Brandon Williams on 2009-04-28
There should be a file on your system called /etc/modprobe.d/options. If you add a line like this:
```
options uvcvideo quirks=16
```
to that file, then the option you want should be used by the system whenever the uvcvideo module is loaded via modprobe.

To edit the file, you will need to run your editor with sudo, as in:
```
sudo nano /etc/modprobe.d/options
```

---

### Post by wawacito on 2009-04-28
Brandon - thank you soooo much for replying.

However - there is no file called "options" in the directory /etc/modprobe.d

I have the following files in that directory:
alsa-base.conf
blacklist-ath_pci.conf
blacklist.conf
blacklist-firewire.conf
blacklist-framebuffer.conf
blacklist-modem.conf
blacklist-oss.conf
blacklist-watchdog.conf
libpisock9.conf

---

### Post by wawacito on 2009-04-28
rather than wait for a reply I just created a file called "options" and put just one line in it "options uvcvideo quirks=16" and rebooted.

At first my computer would not start up - stuck on black screen - I was panicking.

I forced a hard shutdown and turned it on again and now it works! 

Whew!  thanks so much!  Can one of the mod's mark this "Solved"

---

### Post by Brandon Williams on 2009-04-29
Great! I'm glad that worked out. When I read the 'booted to black screen' part, it made me kind of nervous :-)

---

