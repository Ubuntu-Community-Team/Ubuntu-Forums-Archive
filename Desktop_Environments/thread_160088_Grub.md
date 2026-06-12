---
title: "Grub"
date: 2006-04-14
forum: Desktop Environments
---

### Post by subtrakt on 2006-04-14
I just installed windows over top of my ubuntu installation and I'm wondering how to reload grub so I won't have the windows boot loader anymore.  Is this possible with a pre existing ubuntu installation?

---

### Post by oscar on 2006-04-14
So you still have ubuntu installed but the windows install overwrote the bootloader? If so I think you just have to put in the install CD and select "Boot existing installation" or "Rescue installation" or something like that.
There is a command called grub-install which I think should work, though I have never had to use it myself.
When you get into ubuntu open up a terminal and:
```
sudo grub-install /dev/hda
```
changing /dev/hda to whatever device your hard disk is (normally /dev/hda but mine is /dev/sda).
I've just tried it and will see if I can reboot ;)...
[edit] It seems to work [/edit]

---

