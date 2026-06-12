---
title: "Attempting to install 180.29 nvidia driver broke my display."
date: 2009-02-21
forum: General Help
---

### Post by 0bso on 2009-02-21
I had been running the 180.22 beta driver but I wanted to update it to the newer 180.29 stable driver. So I grabbed the 180.29.run file from nvidia's site, dropped over to terminal, stopped gdm, and ran it. Seemed to install ok apart from a message saying there wasn't a package for my kernel and it would compile one (using the latest ubuntu kernel xxx.11 or whatever). 

Now after restarting I get the low graphics mode error. After searching I find I can install the driver via apt. I tried that and it installs and shows up correctly in the hardware driver list but I'm still stuck in low graphics mode and nvidia-config tells me "You do not appear to be running a NVIDIA X driver, run nvidia-xconfig and restart (I've tried this several times with no luck)." 

I tried reverting back to the 177 driver that previously worked fine on this system but it still does the same thing. I've also tried stopping the GDM and running dpkg-reconfigure xserver-xorg but it doesn't change anything. 

Is there any way just to tell it to start over and completely redetect/reconfigure the video settings? I thought thats what "dpkg-reconfigure" was for. 

Card is a 6600gt that I've never had problems running under ubuntu.

---

### Post by whitelinux on 2009-02-21
Re: screwed up trying to upgrade my nvidia graphics driver
0bso, thank you very very much my friend you save me hours, fixed the problem completly.

I did the following as to your instructions:

The solution:

I removed by hand these files: /usr/lib/libGLcore.so.1 which actually is a symlink to libGLcore.so.180.29 (so I removed this file as well) and /usr/lib/xorg/modules/extensions/libglx.so which actually is a symlink to libglx.so.180.29 (also dropped) then I ran the nvidia-uninstall script.

---

