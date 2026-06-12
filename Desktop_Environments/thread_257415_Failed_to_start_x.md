---
title: "Failed to start x"
date: 2006-09-14
forum: Desktop Environments
---

### Post by ATAQ on 2006-09-14
hi, using the synaptic package updater I just updated ,my kernel, rebooted and got the message saying failed to start x server. how can i get around this?

---

### Post by abelthorne on 2006-09-14
Exactly the same problem here. Updated to 2-6-15.26.47 (I think) and X server won't start. Don't tell me there is a broken update *again* !?

---

### Post by ATAQ on 2006-09-14
its annoying mate isnt it. I dunno what to do, is it because of nvidia drivers in the updated kernel would you say? is there any command to roll back?

---

### Post by Lamar on 2006-09-14
> **ATAQ said:**
> hi, using the synaptic package updater I just updated ,my kernel, rebooted and got the message saying failed to start x server. how can i get around this?

I'm getting a "no screens found" error after the kernel image update. As a result, I'm posting on this forum using Lynx... not good. In any case, I tried reinstalling my Nvidia drivers with no luck. Anyone have any ideas on how to fix this?

Just for the record, this makes two updates in a month that breaks the xserver. Ubuntu, being a "user-friendly" Linux distro, should make the xserver a priority. Most people are are new to Linux would not be visiting the forums in Lynx. They would be reinstalling Windows (TM).

---

### Post by ATAQ on 2006-09-14
true, i'm gettin sick of it. If I have to reinstall i'll lose all my stuff

---

### Post by abelthorne on 2006-09-14
An updated version of the kernel will be made available soon (I hope "soon" does mean less than 24 hours...). Then, you'll juste have to do as usual : **sudo apt-get update**, then **sudo apt-get upgrade**.
You won't have to reinstall and lose your stuff.

And you can access the web graphically with a LiveCD, rather than using Lynx. ;)

---

### Post by detgar on 2006-09-14
My X stopped working too. I've fixed it by not using the proprietary nvidia drivers. So try setting the "Options "nvidia"" to "Option "nv"" instead. ATI users might try the vesa drivers, I guess.

---

### Post by nyarla33 on 2006-09-14
Same issue here, after the kernel update.

I then edited /etc/X11/xorg.conf and changed
    Driver		"nvidia"
to
    Driver		"nv"

After that the x server restarted with success.

But no way to reinstall the graphic drivers.](*,)

---

### Post by ATAQ on 2006-09-14
how do i edit the file. what prog do i use from the shell?

---

### Post by nyarla33 on 2006-09-14
> **ATAQ said:**
> how do i edit the file. what prog do i use from the shell?
Use nano

sudo nano /etc/X11/xorg.conf

---

### Post by ATAQ on 2006-09-14
thanks mate, worked. do i just reinstall nvidia driver under apt?

---

### Post by nyarla33 on 2006-09-14
The point is that the proprietary nvidia drivers fail to install for me (x server not starting) after that. 
So I just don't use them till the next update.

---

### Post by ATAQ on 2006-09-14
ya i tried there aswell, so i am just gone back  to the nv driver. Its really bad, these updates should be checked before being made available.
Thanks for the help tho

---

### Post by tophfisher on 2006-09-14
This bit me too... MAN THIS SUCKS.. This is my work system... DANG IT.

Its an easy fix to go change the driver from nvidia to nv and fix the issue, but the Windows people in the office laugh at me when they see what looks like a "Linux Crash".

Bummer.. ](*,) 
-Chris

---

### Post by Lamar on 2006-09-14
> **"detgar"]My X stopped working too. I've fixed it by not using the proprietary nvidia drivers. So try setting the "Options "nvidia"" to "Option "nv"" instead. ATI users might try the vesa drivers, I guess.[/quote]

This didn't work for me. I don't think the free 'nv' driver can handle my modline to support my 1680x1050 resolution.

[quote="abelthorne"]An updated version of the kernel will be made available soon (I hope "soon" does mean less than 24 hours...). Then, you'll juste have to do as usual : sudo apt-get update, then sudo apt-get upgrade.[/quote]

I have no doubt that they will have a fix out soon. The question still remains as to why this update happened. I've grown to really like Ubuntu but I'm beginning to have serious doubts about the QA being done by package maintainers. These xserver-killing updates are not coming from some community-based multiverse repository said:**
> And you can access the web graphically with a LiveCD, rather than using Lynx.

Thanks for the suggestion but I decided to commandeer my wife's computer instead :)

---

### Post by ATAQ on 2006-09-14
What graphics card are you using?

---

### Post by Lamar on 2006-09-14
> **ATAQ said:**
> What graphics card are you using?

I'm using an Nvidia card. Changing the driver to 'nv' rather than 'nvidia' didn't do anything for me. I continue to get a "no screens found" error in my xorg log.

---

### Post by ATAQ on 2006-09-14
check it again to make sure that you saved the file with the driver name change. just to see

---

### Post by seanUSXIII on 2006-09-14
This is one reason I always keep an old kernel available in GRUB, so I know I always have at least one stable kernel #-o

---

### Post by ATAQ on 2006-09-14
i have a few kernels there too but there all seemed to be effected. what kernel you working away on?

---

### Post by Lamar on 2006-09-14
> **ATAQ said:**
> check it again to make sure that you saved the file with the driver name change. just to see

It did save but the free driver, as far as I can tell, doesn't support my native resolution of 1680x1050, nor does it recognize my modeline that forces that resolution. I'm sure that I could load the free driver with a non-native resolution but I'm really not that desperate at the moment. I can wait for the patch.

---

### Post by ATAQ on 2006-09-14
true, sure when its updated there'd be no point in changing back all your settings for the sake of a few hours, i hope! cos i really need glx

---

### Post by Xk2c on 2006-09-14
USN-346-1 provided an updated Linux kernel to fix several security
vulnerabilities. Unfortunately the update broke the binary 'nvidia'
driver from linux-restricted-modules. This update corrects this
problem. We apologize for the inconvenience.

so the fixed update should be available really soon now.

---

### Post by Xk2c on 2006-09-14
yep it is:

The following packages will be upgraded:
  linux-image-2.6.15-26-k7 [2.6.15-26.46 -> 2.6.15-26.47]
  linux-restricted-modules-2.6.15-26-k7 [2.6.15.11-3 -> 2.6.15.11-4]
  linux-restricted-modules-common [2.6.15.11-3 -> 2.6.15.11-4]
  nvidia-glx [1.0.8762+2.6.15.11-3 -> 1.0.8762+2.6.15.11-4]

---

### Post by ATAQ on 2006-09-14
Hey by the way, I just downloaded the Nvidia driver and installed it, and it works fine.
The problem is that the restricted nvidia driver was not updated to the update network yet and the version was not compatible with the new kernel.
I advise downloading the driver in nv driver mode and then reboot with nv disabled so x doesn't start and then install nvidias drivers.

Sweet *** now I can play world of warcraft again

---

### Post by jdong on 2006-09-14
The fixed update is now available. See the forum homepage announcement if you need help installing it.

---

