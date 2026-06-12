---
title: "Only boots into GUI with screen plugged in"
date: 2010-11-24
forum: Desktop Environments
---

### Post by MartinKS on 2010-11-24
Hi,
 I've got a desktop 10.04 LTS installation working nicely, and leave it logged in processing things for me. I log in remotely and don't always leave the screen plugged into the computer. Trouble is when I reboot it without the screen plugged in it will sometimes boot to a command prompt.
 If I turn it off, plug in the screen and turn it on again I get into the GUI as normal. I can't see any settings to change this behavior - what am I missing?

Thanks in advance,
 Martin

---

### Post by asmoore82 on 2010-11-25
This is a semi-Bug.

Great strides have been made in recent years in not having to hard code any Xorg configuration and also modesetting code for graphics hardware is in the process of being moved from userspace to kernel space.

A side effect of "automagic" configuration is that it can't configure what isn't there.

You might be interested in the "Perfect Headless Server" link in my signature, the VNC server configuration described there is totally independent of any graphics hardware.

You don't have to restart completely to get X back though,
you can just log in to the text console and run ```
sudo restart gdm
```

---

