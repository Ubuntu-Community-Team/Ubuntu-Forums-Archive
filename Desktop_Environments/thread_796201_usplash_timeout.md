---
title: "usplash timeout"
date: 2008-05-16
forum: Desktop Environments
---

### Post by DFreeze on 2008-05-16
In my Hardy disk, usplash times out on the 'reading files needed to boot' part. From there it's textmode only. Can I set the timeout a little longer, so I can enjoy the beautiful splash?

---

### Post by DFreeze on 2008-05-19
Anyone?

Usplash times out on the first (throbbing progressbar) part of the boot and I get textmode before it becomes a regular progressbar.

---

### Post by DFreeze on 2008-05-28
I've tried what [this post]("http://ubuntuforums.org/showpost.php?p=452411&postcount=17") suggested, allthough it was written in the Breezy era. I've added the TIMEOUT = 30 statement on different locations in the usplash script, but I still get verbose after 10 seconds. 

How does one interface with usplash now? Anyone here know?

---

### Post by DFreeze on 2008-05-29
Well, I've fixed the problem. I found a [bugreport]("https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/205990") suggesting a fix. The UUID of my swap partition was wrong in fstab and in /etc/initramfs-tools/conf.d/resume. Now the bootsequence stays in the 'reading files needed to boot' much shorter, and the timeout isn't reached. Off course that still doesn't answer my question why I couldn't influence the timeout with a TIMEOUT = 30 (or any number of seconds) in the script in /usr/share/initramfs-tools/scripts/init-top/usplash. 

To whom it may concern ;-)

---

### Post by aashay on 2008-05-30
Same problem here. Also the usplash seems to be rendered at a weird resolution. It looks vertically stretched to fit the screen
EDIT: I tried the solution in the bugreport (uuid for the splash was wrong). It didn't help though
RE-EDIT: Had forgotten to update-initramfs. Works good now. Even fixed hibernate!! A thanks is in order

---

### Post by DFreeze on 2008-06-02
> **aashay said:**
> Same problem here. Also the usplash seems to be rendered at a weird resolution. It looks vertically stretched to fit the screen [...]

I've had a problem with usplash not showing at all (after installing Feisty a yearago), and that was fixed with 

sudo gedit /etc/usplash.conf

and putting the correct resolution in these lines:

xres=1024
yres=768

Do another initramfs update like so:

sudo update-initramfs -u

and that fixed it for me. I don't know if that is what's bugging you, but you could give it a try.

---

