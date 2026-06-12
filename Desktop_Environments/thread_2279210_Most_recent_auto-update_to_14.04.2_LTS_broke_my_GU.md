---
title: "Most recent auto-update to 14.04.2 LTS broke my GUI"
date: 2015-05-21
forum: Desktop Environments
---

### Post by noah19 on 2015-05-21
Hi all,

So I've been running Ubuntu 14.04 on my 64-bit desktop since last fall, with no major glitches. I keep up with the automatic updates, and yesterday okayed one for the Ubuntu core. As far as I could tell, it ran alright, saying the system needed to be restarted for the update to take effect. I postponed that for several hours, and then shut down for the night.

Booting up my machine again this morning, it got as far as the Ubuntu-with-orange-dots-under-it-over-purple-background screen. Then, when ordinarily I would see the login splash, the screen just went black. No GUI. I could type in my password and hear the little drum patter indicating a successful login, but the screen remained black. Help!

With it in this state, I can Ctrl+Alt+F1 into the tty1 window and do text terminal things, but going back to tty7, the screen continues to remain black. I checked the list of running processes, and X is running on tty7, if that means anything.

Here's the most recent update from history.log, the one that I think caused the problem:

Start-Date: 2015-05-20  15:37:00
Commandline: aptdaemon role='role-commit-packages' sender=':1.94'
Install: linux-signed-image-3.13.0-53-generic:amd64 (3.13.0-53.88), linux-headers-3.13.0-53:amd64 (3.13.0-53.88), linux-image-extra-3.13.0-53-generic:amd64 (3.13.0-53.88), linux-image-3.13.0-53-generic:amd64 (3.13.0-53.88), linux-headers-3.13.0-53-generic:amd64 (3.13.0-53.88)
Upgrade: linux-headers-generic:amd64 (3.13.0.52.59, 3.13.0.53.60), linux-signed-generic:amd64 (3.13.0.52.59, 3.13.0.53.60), linux-signed-image-generic:amd64 (3.13.0.52.59, 3.13.0.53.60), linux-firmware:amd64 (1.127.11, 1.127.12), linux-libc-dev:amd64 (3.13.0-52.86, 3.13.0-53.88), linux-image-generic:amd64 (3.13.0.52.59, 3.13.0.53.60)
End-Date: 2015-05-20  15:38:48

What can I do to try and get my desktop GUI back? I would prefer to not reinstall the entire OS, since I have a fair amount of customizations/things installed that I wouldn't like to lose, although I'll do that if I really have to. Ideally I'd like to figure out how to revert whatever changed package or kernel is causing the problem, and pin it at that version, until some later date when hopefully the change would have been fixed.

Thanks for your help!

---

### Post by noah19 on 2015-05-22
Slight update, I tried restarting lightdm with

sudo restart lightdm

in the tty1 terminal, and the screen went from text to black, with the drum patter sound in the background. Presumably this was my context changing back to tty7 with the newly-restarted lightdm, but the same black-screen problem. So, didn't seem to help.

---

### Post by deadflowr on 2015-05-22
I would think that a common reason for something like this to occur is due to a graphics driver not being properly configured for/against the kernel.
To test this hypothesis out boot in the grub menu and select an older kernel.
You can do this at the startup.

(You need to press the shift key (or the ESC key, if using a UEFI install) when the BIOS screen fades away, so that the grub menu will show; this is if you don't normally see a grub menu.
grub is the boot menu, for what it is worth.
From the grub menu you can choose an older kernel; Do not choose one that ends with (recovery mode) or you will go to the recovery mode section)

Since the new kernel is listed as 3.13.0-53 look for one that has a lower number.
Seems your last one was 3.13.0-52 so try/look for that one.

See if changing the kernel helps.


And also do you know anything about your current graphics card?

---

### Post by QIII on 2015-05-22
Hello!

Could you tell us what graphics card you are using?

---

### Post by noah19 on 2015-05-22
@deadflowr

Thanks! I tried booting to 3.13.0-52 from grub (which took some doing, as grub wasn't opening - I had to change the GRUB_HIDDEN_TIMEOUT and GRUB_HIDDEN_TIMEOUT_QUIET fields in /etc/default/grub per [http://askubuntu.com/questions/87409/i-cant-get-grub-menu-to-show-up-during-boot](http://askubuntu.com/questions/87409/i-cant-get-grub-menu-to-show-up-during-boot)) and it happily booted correctly. That's great to see! I guess that confirms that the problem originates with the new kernel. Is there a way to prove it's the drivers not working? Or is a blank screen pretty much a smoking gun for that?

---

### Post by noah19 on 2015-05-22
@deadflowr and QIII,

My graphics card per lspci:

01:00.0 VGA compatible controller: NVIDIA Corporation GK104 [GeForce GTX 770] (rev a1)

I'm currently using the NVIDIA binary driver version 331.113 (nvidia-331 package).

Thanks for the replies, all! I don't know *quite* enough about Ubuntu/Linux to be able to fully troubleshoot this on my own, so your help is invaluable, and will help me get better at figuring out issues on my own :)

---

### Post by deadflowr on 2015-05-23
Hmm, I wonder if your problem is related to this
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331/+bug/1373136](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331/+bug/1373136)

and a more recent duplicate bug here
[https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331/+bug/1457516](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331/+bug/1457516)

---

### Post by noah19 on 2015-05-23
Hmm, possibly, although I didn't get any error messages or anything about the module failing to build.

Following on your suggestion about the driver being the issue, I tried swapping back to the X Org driver (by typing in 'driver' to Dash and opening up Additional Drivers) from Nvidia. When I restarted the system with X Org and the new, latest kernel, everything booted up fine! So definitely a kernel-driver interaction problem. 
 
More interestingly, I swapped back to the Nvidia driver to confirm that that was the problem, and rebooted once again with the newest kernel (3.13.0-53.88) and it actually booted correctly, with my GUI back! So it would now appear to be working fine again (knock on wood). So, to anyone who has the same problem and comes across this thread, I would suggest swapping drivers briefly. I would hazard a guess that the new kernel installation stomped on some value important to the driver install, and swapping away from and back to the driver gets that value reinstated as it should be.

If that's true, of course, every time I get an update (until they figure out what the issue is) my drivers will bork up again... we shall see... But for the time being, the problem is solved, yay :D Thanks for the help everyone!

---

