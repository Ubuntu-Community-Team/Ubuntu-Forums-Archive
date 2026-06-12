---
title: "nvidia installer custom kerel"
date: 2009-04-08
forum: General Help
---

### Post by samrat1985 on 2009-04-08
Hi guys,

Here I go..

**OS**: Intrepid 8.10
**Kernel**: Custom 2.6.28.7-tux9
**Graphic Card**: 9600GT 512 MB
**Driver**: nvidia_linux_x86_180.29_pkg1.run

* Official nvidia-installer x86 180.29 used.

* nvidia-installer gives error (see attachment).

* Irony, I had successfully compiled this specific

nvidia 180.29 month ago using this very custom kernel.

* I had uninstalled the nvidia driver yesterday since I had bought a new gfx 
card 9600GT & the movies I played on 
Ubuntu had weird colors. So I though of uninstalling & reinstalling 
the 180.29 driver. 

* Kernel was made by kernel-package; gcc version 4.3.2

* It had given the same error the first time 
I tried this nvidia-installer on this specific custom kernel but I fixed that by linking

/lib/modules/`uname-r`/build -> /usr/src/linux-headers-`uname -r`.

The original link was pointing towards something else.

* Now it gives the same error even though above mentioned link is corrected!

* The nvidia driver compiles correctly for Ubuntu 8.10 2.6.27.7-generic kernel. 
No errors at all.

* The thing is why can't it build module for custom kernel now if I had built it earlier 
for the very kernel & same driver version!

* Also I had tried dkms in between this whole thing but I removed it even without using it since I found that nvidia-installer gives you '-K' option to build kernel module only if 
you use multiple kernels.

* I have tried --kernel-source-path.

People any help is appreciated

PS: This seems to be similar
[http://ubuntuforums.org/showthread.php?t=1111593&highlight=nvidia+installer](http://ubuntuforums.org/showthread.php?t=1111593&highlight=nvidia+installer)

---

### Post by samrat1985 on 2009-04-09
No one! Help a distressed soul!!

PS: The weird colors in movie playback was fixed. 

Just slide the hue (video options) to 0 
in totem movie player. If this doesn't work then comment all 
"*Option*" @ "*Extensions*" in */etc/X11/xorg.conf* except 
"*Composite*" & "*Xinerama*". Also make a backup just incase!!

---

### Post by knattlhuber on 2009-04-10
What is the error that the nvidia installer returns? (there is no attachment)

---

### Post by samrat1985 on 2009-04-10
Hey Sorry 

foolish of me to overlook the attachment thing!

I had renamed the error file to 'logfile' & it didn't upload giving error 'invalid file' that I had overlooked.

I just solved the error:) The link 

/lib/modules/`uname-r`/build -> "source used to build the kernel"

Ex. 

/lib/modules/`uname -r`/build --> /home/sam/linux/linux-2.6.28.7


PS: attachment added & thanks for trying to help me out.

---

