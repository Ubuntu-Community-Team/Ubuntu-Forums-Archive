---
title: "Virtualbox XP guest, only 600x800 resolution"
date: 2009-06-25
forum: Desktop Environments
---

### Post by windfix on 2009-06-25
I am running an XP virtual machine under virtualbox 2.2.4 with guest additions installed. On my laptop, 1280x800, I only get an 600x800 version of XP.  No other options available from XP's display properties.

When I hook up an external monitor, I can have have 1152x864 in XP's display properties.  (1280x1024 monitor).

Now, when I go back to the laptop monitor, I can keep the 1152x864 resolution displaying now on the laptop screen (requires minor scrolling, cuz the vertical is higher than the laptop screen)

Is there some way to have the higher rez option without going through the PIA of hooking up an external monitor every freaking time?

---

### Post by Villiam on 2009-06-26
Have you tried checking / changing your video adapter's colour depth. 16bit to 32bit or vice versa.

[ubuntu]("http://www.linux-archive.org/ubuntu-user/")

---

### Post by dka on 2009-06-26
You need to install Guest Additions for your XP virtual machine in order for the VM to use the advanced features of your host.  It also enables better mouse and keyboard support along with the variable resolution that you are looking for.

1) Start up your VM.
2) When it is booted, go to the Devices -> Install Guest Additions.
3) Follow the on screen instructions.

* Note: you will need to restart the VM.

Good Luck.

---

