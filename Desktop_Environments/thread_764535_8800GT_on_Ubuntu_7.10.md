---
title: "8800GT on Ubuntu 7.10"
date: 2008-04-24
forum: Desktop Environments
---

### Post by zaz_tekcor on 2008-04-24
After trying for what seems like an eternity, I cannot get my GeForce 8800GT to work. I have searched the forums and google, followed just about every tip I can think of. I've tried with Envy and without. I read a handful of stories about people who can make it work, but I just can't.

Does it actually work?

Using drivers 169.12, up-to-date 32-bit Ubuntu 7.1. When using the "nv" driver, I get an image, but it sucks. 800x600 max, no compiz effects. When using the "nvidia" driver, I get nothing at all. Not even an active black screen, my monitor goes into low power mode as if nothing is happening at all. Using gde, btw.

I had this working with my 7950GT so I've thought about plugging that in as well, but that would require switching the port my monitor is plugged into when I want to switch.

Any help maybe?

---

### Post by chewearn on 2008-04-24
> **zaz_tekcor said:**
> Using drivers 169.12, up-to-date 32-bit Ubuntu 7.1. When using the "nv" driver, I get an image, but it sucks. 800x600 max, no compiz effects. When using the "nvidia" driver, I get nothing at all. Not even an active black screen, my monitor goes into low power mode as if nothing is happening at all. Using gde, btw.

Turn on your sound.  Do you hear the "drum rolls" signifying that Ubuntu is waiting at the log-in prompt (for the moment, ignore the fact that there is no display)?

If ubuntu is waiting at the prompt, go ahead and log-in (typing username <enter and password <enter>).  Does the GUI desktop came back after that?

---

### Post by zaz_tekcor on 2008-04-24
Well now that you mention it, I don't have sound at all. I guess I'll try to hunt down some creative drivers, but I'm not even sure if it's wise to tackle more than one problem at a time.

---

### Post by chewearn on 2008-04-24
How about booting up to safe mode?  After BIOS POST, you see "Press ESC ..." or something like that, press [ESC] key, you should see the grub menu (if you have more than one OS, the grub menu will appear without the ESC message).

Select safe mode, it should bring you to the desktop.  Now, go to:
System > Administration > Login Window > Security (tab)
Check the box for Enable Automatic Login.

Reboot.  See if you can now get to the GUI desktop.  If this is successful, you can then fix the "black screen" during login process:
[http://www.namanb.com/2007/11/ubuntu-710-bootup-resolution-problem.html](http://www.namanb.com/2007/11/ubuntu-710-bootup-resolution-problem.html)

If all goes well, you can go back and disable automatic login.

---

