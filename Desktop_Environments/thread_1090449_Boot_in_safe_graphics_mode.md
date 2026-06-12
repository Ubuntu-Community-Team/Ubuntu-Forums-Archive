---
title: "Boot in safe graphics mode?"
date: 2009-03-08
forum: Desktop Environments
---

### Post by BlackIrish on 2009-03-08
Hi!

I've just installed Ubuntu 8.10 and it seems the old error I had is back: Any time I try to boot in Ubuntu I get "Video Mode Not Supported" on my monitor (This is because I have a Radeon 4850 and these are not supported by default in Ubuntu 8.10, so I need to somehow install the new fglrx drivers).

So, I know that I can fix this if I can boot into Ubuntu with a safe graphics mode (the vesa drivers), but how do I do this?

Because when I click ESC while booting, I only get to select normal and recovery mode, but none of these have any options about a safe graphics mode.

So, how would I do that?

Also, maybe by now someone has figured out a better way to fix this issue? Somehow by installing and configuring fglrx and x by terminal? Or maybe I can somehow manually set the resolution and refresh rate?

Thanks!

---

### Post by jpietari on 2009-03-08
Do you think you could boot up in rescue mode and install the graphics card driver by using apt-get?

sudo apt-get install xserver-xorg-video-ati xserver-xorg-video-radeon

---

### Post by djungelmums on 2009-03-08
Id also like to know how to enter low graphics mode. Its not the same as recovery-mode.

---

### Post by BlackIrish on 2009-03-08
jpietari, yes I booted in rescue mode and went in the terminal as root.

I installed the drivers you said, also downloaded fglrx, and still no go. I also uninstalled compiz, and did an update and dist-upgrade, but still I get "video mode not supported"

But what the silly thing is that, if I put the live cd, and press F4 to choose safe graphics mode, then everything works great! But when I install ubuntu, I can't select this option from anywhere? Or maybe I'm missing something?

---

### Post by BlackIrish on 2009-03-09
I guess no one knows the solution to this? :p

---

### Post by caue.rego on 2009-05-22
Well, I don't know about your issue, but this is a good source to try to solve it: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

