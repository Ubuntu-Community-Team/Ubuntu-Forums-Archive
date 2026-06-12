---
title: "Touchpad not responding after suspending"
date: 2016-01-21
forum: Desktop Environments
---

### Post by ben195 on 2016-01-21
Hi,


This is my first post here, I'm a new Ubuntu user (14.04).


Whenever I come out of a suspend, my touchpad doesn't respond and I have to reboot before it works again.


Looking around for a solution I found that I should edit /etc/pm/sleep.d/0000trackpad to:


#!/bin/sh
case "$1" in
suspend|hibernate)
  modprobe -r psmouse ;;
resume|thraw)
  modprobe psmouse;;
esac


After saving this, suspend just flat out stopped working and nothing happened at all when I sudo pm-suspend.

I have an asus laptop with the Optimus integrated graphics, which have been causing me other issues. I wouldn't be surprised if it had something to do with this too.


Thanks for the help!

---

