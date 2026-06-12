---
title: "Take a look at my GRUB menu and tell me how to clean it up..."
date: 2008-12-16
forum: General Help
---

### Post by PsychedelicWonders on 2008-12-16
Here is a picture of my GRUB menu... looks like there are several duplicates...

Which ones should I clean up and how do I go about doing so?

I am running 8.04 64, but plan on upgrading to 8.10 64, should I do that before cleanign up my GRUB menu?

---

### Post by Izek on 2008-12-16
Have you installed a package through terminal ever after upgrading kernels?

installing any package through terminal should tell you that one or more of the kernels will be removed as they are not being used.

Unless your kernels are all being used.

---

### Post by jocko on 2008-12-16
Just uninstall the two extra kernels. Open up synaptic and search for "linux-image", mark the two old ones (-21- and -19-) for complete removal.

---

### Post by drs305 on 2008-12-16
Take a look at this tutorial on StartUp-Manager. It's a great gui tool to help edit the menu.lst safely. SUM lets you set how many kernels you see (the reason the tutorial was originally composed) and lots of other tweaks such as menu dispay timeout, default OS or kernel, etc.

Here is the link:
[HOWTO: Grub Menu Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

I would recommend you keep 2 kernels - the one you are using and one which worked in the past. SUM alters the number you see in the startup menu but does not remove them from your system. For that, you have to use synaptic or do it via the command line. It's all covered in the tutorial.

On my menu, I keep the current kernel, the current recovery mode, and one older kernel option. You don't even have to see the menu - you can allow grub to boot automatically without ever seeing the menu, or you can let it display for only a second or two so you can hit ESC to halt the progress and select the option you want.

---

### Post by PsychedelicWonders on 2008-12-19
> **drs305 said:**
> Take a look at this tutorial on StartUp-Manager. It's a great gui tool to help edit the menu.lst safely. SUM lets you set how many kernels you see (the reason the tutorial was originally composed) and lots of other tweaks such as menu dispay timeout, default OS or kernel, etc.

Here is the link:
[HOWTO: Grub Menu Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

I would recommend you keep 2 kernels - the one you are using and one which worked in the past. SUM alters the number you see in the startup menu but does not remove them from your system. For that, you have to use synaptic or do it via the command line. It's all covered in the tutorial.

On my menu, I keep the current kernel, the current recovery mode, and one older kernel option. You don't even have to see the menu - you can allow grub to boot automatically without ever seeing the menu, or you can let it display for only a second or two so you can hit ESC to halt the progress and select the option you want.

Let me ask this, I plan on upgrading to 8.10 very soon... should I upgrade first and then clean out my GRUB?

I want to see the GRUB menu since I dual boot, I just want to clean it up a little.

You said: I would recommend you keep 2 kernels - the one you are using and one which worked in the past.

AFAIK, all of the kernals have worked in the past.

I dont even know how I got multiple kernals to begin with.

I would assume I should keep -21 also since that seems to be the last version before my newest one?

So does this mean I have Ubuntu installed 3 times on my computer?

is that how it works?

---

### Post by redilyn on 2008-12-19
I would upgrade first and then clean your menu.lst.

Would make more sense since more kernels will be installed.

Myself, I only keep the current kernel that im using plus one other kernel and recovery mode.

---

### Post by FuturePilot on 2008-12-19
> I would assume I should keep -21 also since that seems to be the last version before my newest one?
Yes, keep -22 and -21. You can remove -19

> So does this mean I have Ubuntu installed 3 times on my computer?

is that how it works? 
No, as part of the normal updates, every now and then there will be an update to the kernel for security fixes, bug fixes, etc. Sometimes it requires an ABI bump which is denoted by the last number, in this case -19 -21 -22. You only have 1 Ubuntu installation, but you have multiple kernels installed.

---

