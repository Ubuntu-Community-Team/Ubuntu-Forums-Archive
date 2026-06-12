---
title: "NVidia vs Resticted"
date: 2007-12-19
forum: Desktop Effects &amp; Customization
---

### Post by noisebug on 2007-12-19
What is the difference between the Gutsy restricted driver, and the driver from the Nvidia website?
I have a 8800GTX, and after installing the NVidia drivers I got the white screen of death, but thats beside the point.

My point is, I installed the NVidia drivers thinking it would enable OpenGL, but it didn't. While I search for an answer to try and recover from the white screen, can someone tell me what the difference between the two is?

Maybe if I understand that I will have a better grasp on the problem.

Thank you,
NB

---

### Post by reckless2k2 on 2007-12-19
i believe the nvidia site is more current.

---

### Post by noisebug on 2007-12-19
Does this mean the restricted drivers were made by NVidia in the first place?

---

### Post by FuturePilot on 2007-12-19
> **noisebug said:**
> Does this mean the restricted drivers were made by NVidia in the first place?

The Nvidia drivers in the repos are the same ones from Nvidia only packaged specifically for Ubuntu. Though the repos are frozen at release so the version in the repos most likely is not the latest version.

---

### Post by noisebug on 2007-12-19
I understand, thank you. So installing the one from NVidia was the right thing to do. I'm starting to think this is not a problem with my drivers, but with Compiz itself.

Cheers

---

### Post by dabl on 2007-12-19
The current released version of the binary driver, 100.14.19, is the same whether from the nvidia-glx package or the Nvidia download site.

But, there are quite a few options for use with xorg, and some of them may make a difference with your white screen issue. They are listed in Appendix B here:

[http://us.download.nvidia.com/XFree86/Linux-x86_64/100.14.19/README/chapter-06.html](http://us.download.nvidia.com/XFree86/Linux-x86_64/100.14.19/README/chapter-06.html)


Another thought -- if you're feeling adventuresome, you might want to give the beta Nvidia driver 169-04 a spin:

[http://www.nvidia.com/object/linux_display_amd64_169.04.html](http://www.nvidia.com/object/linux_display_amd64_169.04.html)

note this is the 64-bit package.  There is a 32-bit package as well.

:popcorn:

---

### Post by rsambuca on 2007-12-19
The 8800 series definitely work better with the nvidia beta driver, which requires manual installation from the link dabl gave you.

---

### Post by noisebug on 2007-12-19
Thanks guys. I've tried all the instructions, but none of them work. Its not my drivers, theres something up with Compiz. I uninstalled NVidia drivers, installed my old drivers that use to work, but the white screen is still there. I've uninstalled old, installed new, etc etc. I'm starting to think I need to do a clean install since nothing seems to be working.

---

### Post by LT72884 on 2007-12-20
> **noisebug said:**
> I understand, thank you. So installing the one from NVidia was the right thing to do. I'm starting to think this is not a problem with my drivers, but with Compiz itself.

Cheers
yes beryl does the same thing to me and i have tried both the restricted and ones from nvidia. what i did to revert was ctrl+alt+F1 to get to a tty screen and then i did a reboot and then everything was fine. but once i enable compiz it jacks it all up. thats why i never have compiz or beryl start at start up. even my regular desktop effects dont work.

---

