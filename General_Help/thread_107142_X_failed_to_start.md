---
title: "X failed to start"
date: 2005-12-22
forum: General Help
---

### Post by pjman on 2005-12-22
Hello,

I'll just say this right now, I'm a newbie and I think I broke my Ubuntu install. If you can help me revive my PC I will be very happy! 

Yesterday I was trying to compile Truecrypt which led to my breaking of Ubuntu.

I have Kernel 2.6.10 installed and Truecrypt would not compile. It wasn't finding correct modules or library's to finish. The error message kept pointing to a sub folder something like /usr/src/linux-header-2.6.10/linux-header-2.6.9. I thought it was kind of odd that it was still pointing to 2.6.9 even though I had 2.6.10 installed through he automatic updates. Through Synaptic I uninstalled the linux-headers that were labeled with 2.6.9. While I was at it I thought it was a good time to learn how to compile and install a new kernel (2.6.14.4). I got through compiling it and not installing it. 

I shut down my laptop and now when I booted up this morning I get an error the GDM cannot start and to check /var/log/Xorg.0.log for more information. I looked through it and it looks like something can't find a lot of files... maybe it was from uninstalling the 2.6.9 linux-headers? 

Can anyone help me fix this using a live CD since I do not have network connection now from the terminal.

Thank you!
pjman

Attached is my /var/log/Xorg.0.log file.

---

### Post by BathroomNinja on 2005-12-22
Can you boot up using failesafe from the grub menu?

---

### Post by pjman on 2005-12-22
[QUOTE=BathroomNinja]Can you boot up using failesafe from the grub menu?[/QUOTE]

Yes, but it's pretty much like booting up using the regular option and getting past the X failure error. Once I get past the error I can log in using the terminal but I don't have network connectivity.

---

### Post by pjman on 2005-12-22
I go it to work!! Sorta.. I just installed the 2.6.14.4 deb file that I complied yesterday. Now GRUB shows 2.6.14.4 and 2.6.10. 

I'd like to uninstall 2.6.14.4 and 2.6.10 and do a clean install of 2.6.10 from Ubunu's repositories. Can anyone tell me how to do this? After this I'm going to stay away from compiling kernels for a while :???: 

Thank you!

---

### Post by pjman on 2005-12-22
I figured it out. I installed the 2.6.10-686 kernel from synaptic and I was able to remove the old ones :-)

---

