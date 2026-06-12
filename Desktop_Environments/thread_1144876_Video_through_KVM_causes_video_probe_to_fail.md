---
title: "Video through KVM causes video probe to fail"
date: 2009-05-01
forum: Desktop Environments
---

### Post by a42n81 on 2009-05-01
When I install Ubuntu, or even boot from a live CD, I get a warning during boot that video is not kosher, then I wind up with 800x600 as the best the video can do.

Note that 6.06 worked (and created an 'interesting' xorg.conf, (lots of x=y lines) whereas the later distros I have tried (8.4, 8.10 and 9.4) create 'boring' xorg.confs (basically a few x=default lines) and did not work through the KVM.

I am using an old (more than 5 yrs) Cybex SwitchView 4-port KVM.

When I connect the computer directly to the keyboard, video and mouse, I get the video options that I should. Then I reconnect the computer through the KVM and I'm back to 800x600.

Reminds me of the Dr's joke: Doctor, doctor, it hurts when I do this ... Then don't do that.

But I have four computers and I don't want four mice and four keyboards and four monitors.... And I do like 1024x768 resolution.

---

### Post by jtb_90 on 2009-05-01
You can search this forum on the how to as I'm no pro, but you can manually edit the xorg.conf file or whatever it's called and tell it to view at 1024x768.

---

### Post by a42n81 on 2009-05-01
I tried futzing with xorg.conf on one machine. I could not get it to work. One thing I tried was to install 6.6 on the machine (which did work, nice video at 1024x768 which is all the KVM supports). I copied off the xorg.conf, reinstalled 8.10 (the latest at that time) and used the 6.6 xorg.conf. The machine in question has an Intel D945GLCF2 Little Falls motherboard. I remember I had to change the specified driver, but still could not get the same resolution in 8.10.

---

