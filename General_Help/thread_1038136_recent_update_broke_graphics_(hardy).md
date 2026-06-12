---
title: "recent update broke graphics (hardy)"
date: 2009-01-12
forum: General Help
---

### Post by loserboy on 2009-01-12
hey there,

there were some updates on jan. 9th that I installed including I think a kernel update. upon rebooting it gave me the "running in low graphics mode" error, I let it continue in vesa and when I got to desktop I went to nvidia and downloaded the 181.22 driver and installed it via command line as required, after rebooting it seemed to make no difference so I let it start in vesa again and tried to enable the restricted drivers... now when I start i dont get the low graphics warning and the desktop sorta loads, but freezes after it's finished or only partially loads then freezes.

I've tried recovery>fix x but that doesnt help.
I tried booting into an older kernel but same problem.

Should I try to purge all drivers and start fresh or something?

thanks
mike

---

### Post by gettinoriginal on 2009-01-12
definetly get rid of 181, 177 seems to be the stable one.  This is from another thread:

nvidia driver
For some (unknown to me) reason nvidia driver version 180 just couldn't find my nvidia 6600GT vga, it kept telling me that no nvidia VGAs found. The solution is quite simple this time too - just use 177 version driver, which can be installed this way:

```
sudo apt-get install nvidia-glx-177
```

---

### Post by CRIMPS on 2009-01-13
It seems there are others having this problem as well as seen in this [[COLOR="Red"]post.[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1033446")  I have no idea what I should do in order to get any of the NVidia drivers that I have installed (versions 173 and 177) enabled.  

Maybe this is more related to the kernel update and less about a recent update to the NVidia driver?

---

### Post by loserboy on 2009-01-15
> **gettinoriginal said:**
> definetly get rid of 181, 177 seems to be the stable one.  This is from another thread:

nvidia driver
For some (unknown to me) reason nvidia driver version 180 just couldn't find my nvidia 6600GT vga, it kept telling me that no nvidia VGAs found. The solution is quite simple this time too - just use 177 version driver, which can be installed this way:

```
sudo apt-get install nvidia-glx-177
```

ok I'll give that a shot, but should I remove old nvidia drivers and if so, how?

also I guess I should have mentioned that I have a geforce 7800

---

### Post by loserboy on 2009-01-15
> **CRIMPS said:**
> It seems there are others having this problem as well as seen in this [[COLOR="Red"]post.[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1033446")  I have no idea what I should do in order to get any of the NVidia drivers that I have installed (versions 173 and 177) enabled.  

Maybe this is more related to the kernel update and less about a recent update to the NVidia driver?

as far as I know whenever you manually install the drivers from nvidia's site that they will break on each kernel update (at least thats what nvidia says)

---

