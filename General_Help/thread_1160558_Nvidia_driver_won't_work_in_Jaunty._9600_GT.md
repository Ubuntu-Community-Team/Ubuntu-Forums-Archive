---
title: "Nvidia driver won't work in Jaunty. 9600 GT"
date: 2009-05-15
forum: General Help
---

### Post by mac9416 on 2009-05-15
Hello, ya'll!

    I have an Nvidia 9600GT gfx card for which I downloaded and installed the driver from Nvidia's website. All went well in Intrepid, but when I installed Jaunty and installed the driver on it the next time I booted up I got the GDM failed to start screen. It was simple enough to revert to the old xorg.conf and fix everything, but that leaves me without desktop effects. Any suggestions?

Thanks!
-mac

---

### Post by Sub101 on 2009-05-15
Have you checked the proprietary drivers in System==>Admin==>Hardware Drivers?

It might well be the case there isnt one available yet.

---

### Post by Kareeser on 2009-05-15
Did you make sure to remove the older nvidia graphics driver before installing the new one?

---

### Post by mac9416 on 2009-05-15
Thanks, guys.
Sub101, my box is offline, so whatever is there I would not be able to download.
Kareeser, yes it was installed on a fresh install of Jaunty. I will probably end up removing my current driver to install another, how do I do that?

---

### Post by mac9416 on 2009-05-15
Is nvidia-glx-180 what I need? Do I also need nvidia-180-kernel-source?

---

### Post by mac9416 on 2009-05-15
A fellow on the IRC told me that nvidia-glx-180 would do the job.
Thanks, Magician! ):P

---

### Post by mac9416 on 2009-05-16
So, I installed nvidia-glx-180 and enabled it in Hardware Drivers. When I rebooted, it was disabled and said another version of the same driver was installed -- obviously the driver installed by th Nvidia .run. How do I get rid of the .run and replace it with the .deb?

---

