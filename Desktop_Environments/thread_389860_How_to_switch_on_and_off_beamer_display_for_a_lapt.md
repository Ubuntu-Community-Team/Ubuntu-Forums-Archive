---
title: "How to switch on and off beamer display for a laptop?"
date: 2007-03-21
forum: Desktop Environments
---

### Post by puqing on 2007-03-21
My Presario v3000 laptop has an Intel 945 video chip. On windows, by pressing the <Fn-F4> key, display switches between three modes: LED+CRT, LED only, CRT only. But I found that, the key doesn't work on ubuntu by default.

After some searching and trying, I finally make the CRT output work. My solution is actually rather simple. Just by adding the following two lines in 'Section "Device"', the CRT output works:

Option    "MonitorLayout"   "CRT,LFP"
Option    "Clone"   "True"

However, I still have three questions:

1. Since the CRT port has been working, I guess that if I connect it with a beamer, the beamer should also work. Am I right? Since I don't have beamer at hand, so I can't try it now. 

2. Is there any performance drop by switching on CRT output?

3. Is there a convenient method to switch on and off CRT output, without restarting X server?

Thanks in advance!

---

### Post by Toufik on 2007-04-17
Add this line:
        Option    "DevicePresence" "true"
it will only start if there is something connected

To switch from a display to another: 
$ sudo apt-get install i810switch

$ i810switch crt on
or
$ i810switch crt off

If the image is not correct, try to change your resolution to something more usual : 1024x768 for instance

See [http://ubuntuforums.org/showthread.php?p=2467338](http://ubuntuforums.org/showthread.php?p=2467338)

---

