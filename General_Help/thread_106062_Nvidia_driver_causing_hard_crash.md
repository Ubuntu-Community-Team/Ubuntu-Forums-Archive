---
title: "Nvidia driver causing hard crash"
date: 2005-12-19
forum: General Help
---

### Post by nikopol on 2005-12-19
Have been trying to solve this one for hours but no luck. I have  geforce4 MX 440 ( 0000:01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] (rev a4)) but trying to use any Nvidia driver with it causes GDM to crash and Linux to become completly unresponsive. Not nice!

GDM often only gets so far as printing a few lines of the splashscreen until death ensues. I've tried everything (dpkg-reconfigure  fontconfig brought nothing) so I'm really giving up.

attached it my xorg log of a crashed session. 
Any pointers please?

---

### Post by 23meg on 2005-12-19
Are you using the composite extension? If so, try specifying ```
Option AllowGLXWithComposite "True"
``` in the "Device" section of your xorg.conf file.

The line below also indicates there might be something wrong with your driver installation: ```
(EE) Failed to initialize GLX extension (NVIDIA X driver not found)
``` Is your card supported by the "nvidia" driver? How exactly did you install it?

---

### Post by bb002 on 2005-12-19
When you say any nVidia driver to you mean both the open-source "nv" driver and the proprietary driver "nvidia"? I know that my system won't get past GDM if i use the open source "nv" driver on my GeForce 6800 but runs just fine on the "nvidia" driver.

Posting the file /etc/X11/xorg.conf would be of some help too.

---

### Post by 23meg on 2005-12-19
I mean the proprietary driver; that's why I put it in quotes. Yours is a different matter; the OP's card is an old one and may not be supported by the proprietary driver, whereas yours is a recent one that will only work with the proprietary driver.

---

### Post by carlos.gil on 2005-12-21
I have a similar problem with the same video card. When I install and enable the nvidia-glx driver ( while following the instructions in he ubuntu guide) my x-session chashes and a text-based window appears telling me that there is no configuration file for the x.org session. Any ideas to solve my problem?

Carlos Gil

---

### Post by nikopol on 2006-01-26
Oops - sorry about the late reply. Thanks for the help. Didn't get the problem resolved sadly - just not sure what the problem is but didn't have that much time to solve it so had to leave the computer with the nv driver. Doubt anyone will notice since the computer is supposed to only be used for checking email, wordprocessing, and the web...

---

