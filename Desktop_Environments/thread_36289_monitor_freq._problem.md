---
title: "monitor freq. problem"
date: 2005-05-22
forum: Desktop Environments
---

### Post by dislektik on 2005-05-22
hello

i've got my kubuntu linux (5.04 release) running with slovak localization. the problem is: every time computer boots up and starts kdm (xorg), i get message "freq. out of range" on my lcd. after killing xorg (pushing ctrl-alt-backspace), xorg and kdm restarts and everything is fine.

kdm starting manualy (not immediately after booting, but running /etc/init.d/kdm start) xorg starts properly.

i've tried not to load DDC module and ignore EDID (by editing xorg.conf), but that doesn't really help. looking into logs doesn't bring any light neither.

vga: nvidia geforce2 mx
drivers: standart kubuntu drivers installed (using [http://www.ubuntuguide.org/#installnvidiadriver](http://www.ubuntuguide.org/#installnvidiadriver))

i'm clueless. any ideas?


Luboss

---

### Post by netrattler on 2005-05-22
You don't have a  HorizSync or VertRefresh rate in your xorg.conf file under your monitor section. This is what is causing your problems. Your monitor section should look something like this. Do not use my HorizSync or VertRefresh rate settings or you could damage your monitor. If you have the user manual to your monitor it should tell you your HZ and Vert sync. If not just go to the companies website that made your monitor and download the user manual for it. Hope this helps.

Monitor section under my xorg.conf

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-49
        VertRefresh     43-72
EndSection

joe

---

### Post by dislektik on 2005-05-23
LCD monitors don't need HorizSync and VertRefresh in xorg.conf...

To be sure I tried to set it, but it didn't work.   

Problem is still here...

---

### Post by netrattler on 2005-05-23
The only other suggestion I can recommend is download a copy of the knoppix livecd or mepis livecd and copy the xorg.conf from that and see if that works for you. That way you can compare them and see what's different. Looking at the rest of your xorg.conf file I cannot find anything else that's wrong.

Joe

---

### Post by jookie on 2005-06-05
Shoot, the same problem here... When X.org starts automatically I just got the "Frequency out of range" on my LCD. Running on the Slovak localization... 
The previous instalation was OK, but it was done by installing the english version and then the i18 packages. This one was installed as Slovak from the start... No settings in xorg.conf does help, xorgcfg could not fix it either.

---

### Post by skoal on 2005-06-05
If you're using the DVI port, you might want to use this NVIDIA option:

Option "ConnectedMonitor" "DFP"

---

### Post by jookie on 2005-06-06
This Option "ConnectedMonitor" "DFP" didn't help... anyhow... on [http://www.abclinuxu.cz](http://www.abclinuxu.cz) (exactly here: [http://www.abclinuxu.cz/blog/Soptikovo_K_ubuntu_trable/2005/4/11/83240](http://www.abclinuxu.cz/blog/Soptikovo_K_ubuntu_trable/2005/4/11/83240)) it says that if you install the Kubuntu in Slovak language with Slovak localization, then the finishing of the instalation will fail (they say that this is a documented bug) and the X's will fail to display at the first time after boot-up. 
Their solution is to install it in English as english version and then install the localization packages - then it's OK (as they say).

---

