---
title: "Problems with Nvidia (xorg module) &amp; Wine (sound &amp; Directx) &amp; Drives (partitions)"
date: 2006-09-05
forum: Desktop Environments
---

### Post by snow93 on 2006-09-05
Hello everybody. I am new to Ubuntu, having installed it two days ago. I am relatively new to linux- I install Fedora Core 5 a few months ago, and it broke, which is why I switched to Ubuntu.
:-k 
I have weird problems with my Nvidia driver. The apt nvidia-glx package didn't work, so I installed nvidia's own .pkg2.run file (and uninstalled nvidia-glx) (NVIDIA-Linux-x86_64-1.0-8774-pkg2.run). It said it could not find the Xorg library path, so it installed them in /usr/lib/xorg/modules. Nvidia then worked, so I installed the handy Nvidia-settings program, following some instructions to create a file for it look at. Then I rebooted my comp, and no display appeared, and on tty1 when I typed "sudo startx" it said the driver version (8774) did not match the xorg module version (766?). Perhaps this was left over from the nvidia-glx thingy?
Then I reinstalled the pkg2.run and it works, but when I restart my computer it happens again. And Nvidia0settings doesn't show up.

On Wine, sound doesn't work, as it cannot find
> err:module:load_builtin_dll failed to load .so lib for builtin L"winealsa.drv": libasound.so.2: cannot open shared object file: No such file or d    irectory
err:module:load_builtin_dll failed to load .so lib for builtin L"winearts.drv": libartsc.so.0: cannot open shared object file: No such file or di    rectory
err:module:load_builtin_dll failed to load .so lib for builtin L"wineesd.drv": libesd.so.0: cannot open shared object file: No such file or direc    tory
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack

I have the first 3 files (I don't know about libjack.so) in /usr/lib/, and I thought wine might be looking for them in lib32, so I pu symlinks there. Where is wine looking for them and what do I do about libjack? Also, how do I get wine to use alsa?

With Wine and directx, wine just seems to not have it. Is there some way of enabling it? Games which are on Winehq's platinum list just say "failed to intialize directx" and quit.

And finally, with my Hard drives.
I have 20gb IDE drive for Ubuntu, a 30gb IDE drive for (not working) Fedora, and an 80 gb SATA disc for WinXP (somewhat dead, unhappy and/or sulking. That's the OS, not the drive:p ). (and a 60gb removable vfat hdd)
I used the nice partition shrinker in the Ubuntu installer to make a tiiiny bit of space on the SATA disc for no particular reason.
At the moment, I can't access it. The Filesystem shows up as "unformatted", the second partition doesn't show up at all. I can't access it. Could some one advise if I should somehow use ntfsprogs or chroot, and if so, how.

In advance thanks for any help anyone can give on any of these problems.
Snow93, Cambridge, UK.

---

