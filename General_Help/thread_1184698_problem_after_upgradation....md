---
title: "problem after upgradation..."
date: 2009-06-11
forum: General Help
---

### Post by prabhanjan2906 on 2009-06-11
i upgraded my ubuntu 8.10 to 9.04. after my computer restarted i found that the mouse was not moving. it was not logging me in. it would get hanged at the start up. it was showing in the menu.lst file that the ubuntu 9.04 kernel ends with ro quiet splash. my kernel is 2.6.27-7. is my kernel stable?

---

### Post by akakingess on 2009-06-11
You may need to post more info, what type of system are you running, 32-bit or 64, mouse, computer specs if possible, what type of install did you do?  If you could answer some of those questions some others may be able to help, I just know that in my previous posts it always helps to put in as much info as you can about your system.

akakingess

---

### Post by prabhanjan2906 on 2009-06-11
i am running on a 32-bit system. i installed from the boot(install ubuntu option). i inserted ubuntu cd and in the boot and from the option "try ubuntu without making any changes to my computer" i checked the menu file.

---

### Post by akakingess on 2009-06-11
I am a little confused, did you just run it as a Live CD, or did you actually do the install, cuz the "try ubuntu without making any changes to my computer" option means that you are just running the Live CD, and if that isn't working then usually not a good idea to do a full install/upgrade til you look more into the supported hardware/known issues sticky which should be at the top of this forum. Not trying to pawn you off, but I am farely new to Ubuntu and Linux and that is about what I know, just confused as to whether you did the install or are running the Live CD.

akakingess

---

### Post by ibuclaw on 2009-06-11
Ever since the 2.6 series was released, all Linux kernels have been considered as stable releases.

How did you upgrade Ubuntu from 8.10 to 9.04?
Is this your Laptop, or Desktop?
Have you tried another mouse?

Answering these in some detail may help with finding the root of your problem.

Regards
Iain

---

### Post by prabhanjan2906 on 2009-06-11
well actually my mouse is proper.No i did not try with another mouse but its working fine in windows.after i enter user name and password my comp will get stuck there itself. i upgraded it from update manager. this is my desktop. how to differentiate stable and unstable kernel?

---

### Post by ibuclaw on 2009-06-12
> my kernel is 2.6.27-7.
The kernel version in Ubuntu Jaunty is **2.6.28**

> **prabhanjan2906 said:**
> well actually my mouse is proper.No i did not try with another mouse but its working fine in windows.after i enter user name and password my comp will get stuck there itself. i upgraded it from update manager. this is my desktop.
So you have a PS2 Mouse. It's working fine in Windows, and Ubuntu freezes every time you login to your account, but everything works fine in the login screen.

Try the following steps:
[LIST=1]
[*]If you have an ethernet cable, connect your desktop to your router.
[*]Reboot, and select the "Ubuntu Recovery Console" in the boot-up menu.
[*]When the Recovery Menu loads, select "**Fix X**" using the arrow keys, and press Enter when highlighted. (Note: name of menu item may have a slightly differing name).
[*]Once that has finished and you return to the Recovery Menu, select "**Root with Networking**" and press Enter.
[*]When you drop to the shell, type in the following:
```
apt-get update
apt-get dist-upgrade
apt-get clean
```
[*]Then type in **reboot** to reboot your machine, let it boot up Ubuntu as normal, then try logging in again.
[/LIST]
> how to differentiate stable and unstable kernel?
The development model used to be "Even number = stable" and "Odd Number = testing", but this is not used anymore, so you needn't worry about it.

The kernel is stable ... the software running ontop may be the reason of fault here.

Regards
Iain

---

