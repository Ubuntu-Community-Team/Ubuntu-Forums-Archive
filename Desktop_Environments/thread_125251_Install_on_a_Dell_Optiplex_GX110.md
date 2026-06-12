---
title: "Install on a Dell Optiplex GX110"
date: 2006-02-03
forum: Desktop Environments
---

### Post by txwylde on 2006-02-03
I have an old Dell Optiplex that I got for free. I disabled the onboard video and installed a 16 meg PCI Video card (SIS chipset). My problem is that when I go to try and install Unbuntu, it goes to start GNOME and then the screen goes blank. I believe the video display settings are incorrect when Ubuntu was hardware detecting. Is there a way to manaully configure my video card when installing Ubuntu? Ironically Mandiva works fine as does Zandros and PC BSD 6.0. 

Thanks!
Bill

---

### Post by wbmj on 2006-02-04
You may want to try "dpkg-reconfigure xserver-xorg"

---

### Post by txwylde on 2006-02-08
I dug a little deeper. The Dell Optiplex has an onboard video card that you cant disable in the BIOS. Its either on or its set to detect. I had a 16 meg PCI videoc ard I was using. When Ubuntu installed itself, it found the onboard video and set up the drivers for that card. I got a prompt and did lpci -x and found out that X was set up WRONG. I tried playing with the XFREE86-Config4 file but couldnt get it to work. I pulled the card and changed everything back and it worked.

---

### Post by spitfireNoob on 2006-02-08
I have the same PC and I installed Ubuntu 5.10 fine too. Had lots of trouble with the wireless network cards though, so gave up on that.

Have you checked to see if you're running accelerated graphics yet?  Try running glxinfo and see if direct rendering is 'yes'.  If it is, perhaps you can supply details of your X configuration file? I've downloaded the Intel RPM (and installed with 'alien') but I cannot figure out how to get X using the new executable 'XFCom_i810' that was placed in /usr/X11R6/bin...  any ideas?

Nice little PC by the way (if it's the SFF version). Cheers!

---

