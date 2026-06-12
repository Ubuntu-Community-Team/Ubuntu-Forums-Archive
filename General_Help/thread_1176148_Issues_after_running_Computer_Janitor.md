---
title: "Issues after running Computer Janitor"
date: 2009-06-02
forum: General Help
---

### Post by kevindubrow on 2009-06-02
Hi, I ran the program Computer Janitor and it broke my sound. I noticed that a package that was removed, alsa-driver-linuxant_1.0.19.2_all.deb, probably needed to be reinstalled to get my sound back. I downloaded the .deb again, but if I try to install it, it never finishes the setup. 

If I run it in the terminal, this happens:

Setting up alsa-driver-linuxant (1.0.19.2) ...
Building modules for the 2.6.28-11-generic kernel, please wait...

It never gets past there. I was using a workaround to get sound working because Ubuntu does not have sound out of the box on my HP Mini. Can someone help me figure out how to install this .deb? I can't update my computer without reinstalling this... I get this error in the terminal: E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

Thanks in advance for any help!

---

### Post by mb_webguy on 2009-06-02
Well, have you tried running "sudo dpkg --configure -a" in the terminal?

---

### Post by kevindubrow on 2009-06-02
Yeah, thats another way that I try to install the .deb and I get the same results.

--Edit--
Whoops, I guess it just needed A LOT of time to install. I had that package installing for 45mins last night without anything happening, I let it run all night and I just noticed that it actually installed. Thanks a lot for your help!

---

