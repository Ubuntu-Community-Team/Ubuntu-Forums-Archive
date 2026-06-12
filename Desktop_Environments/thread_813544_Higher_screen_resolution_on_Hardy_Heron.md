---
title: "Higher screen resolution on Hardy Heron"
date: 2008-05-30
forum: Desktop Environments
---

### Post by ArtPulse on 2008-05-30
Hey there. I know there are tons - TONS - of threads like these, but after 20 mins on Google I just couldn't find anything related to it :S.

When I had problems, I've spent hours on Debian or Ubuntu with *dpkg-reconfigure xserver-xorg*. But that won't do the trick anymore! as pretty much of what I can configure there now is the keyboard :S. The xorg.conf looks quite empty as only a third part of what I used to see is there. Dunno where to look anymore! =(

Thing is, it's a Samsung SyncMaster 550v, it should allow 1024x768@60 but the max is 800x600@60 =( I need to configure that computer for 1024 :S as it was on Gutsy (I've just upgraded it - well, clean installed, the alt inst upgrade CD wont work neither: hardy has just given me headaches on all computers so far T_T i miss gutsy at some moments).
The Administration > Screens Manager is gone as well, from Gutsy :S

All solutions I find are for Gutsy ¬¬ I know how to on gutsy, i just had to edit existing data...
Any help? =(

---

### Post by vvvjr on 2008-05-31
Though my solution is non standard, I moved my /etc/X11/xorg.conf to a diff file and killed xserver. when it start xserver again it askes for settings properly. so I was able to configure my lcd settings and driver options properly this time.

> **ArtPulse said:**
> Hey there. I know there are tons - TONS - of threads like these, but after 20 mins on Google I just couldn't find anything related to it :S.

When I had problems, I've spent hours on Debian or Ubuntu with *dpkg-reconfigure xserver-xorg*. But that won't do the trick anymore! as pretty much of what I can configure there now is the keyboard :S. The xorg.conf looks quite empty as only a third part of what I used to see is there. Dunno where to look anymore! =(

Thing is, it's a Samsung SyncMaster 550v, it should allow 1024x768@60 but the max is 800x600@60 =( I need to configure that computer for 1024 :S as it was on Gutsy (I've just upgraded it - well, clean installed, the alt inst upgrade CD wont work neither: hardy has just given me headaches on all computers so far T_T i miss gutsy at some moments).
The Administration > Screens Manager is gone as well, from Gutsy :S

All solutions I find are for Gutsy ¬¬ I know how to on gutsy, i just had to edit existing data...
Any help? =(

---

### Post by ArtPulse on 2008-05-31
I've stopped gdm, moved the file, then started gdm again, yet no dialog nor anything came up :S...

might I add: that computer has an integrated graphics card, and a pretty bad one I think xD no restricted drivers to install... Compiz won't work =P that is not important, guess it doesn't has 3D acceleration. But I need to set things to 1024x768@60 =(

---

### Post by justaguylinux on 2008-05-31
dont know if this will help but under add/remove install intell 915 patch and restart the xserver that alowed the higher setting for me with vcrd on motherboard.

---

### Post by RealG187 on 2008-05-31
Goto recovery mode from grub and type "sudo dpkg-reconfigure xserver-xorg" at promt, just BS through the options until you get to refresh rate, the best bet is to chose "medium" it displays the display modes.

---

### Post by ArtPulse on 2008-06-01
I... I... am not sure what i've done xD I've added a few lines at xorg.conf after half hour of searching... added the mode "1024x768@60" at two places and it worked o.O lol I still dunno why, after so many people having these problems, they haven't come up with a "force resolution" checkbox, up to the user's risk, for the ones that know what they're doing...

it's not my computer so I can't paste the conf file now >.< for those who might have the same problem... sorry... If anyone does, ask, and i'll take the moment to do so xP. PM me, whatever.

anyways, thanks everyone!! =P

---

### Post by RealG187 on 2008-10-12
Apparrently the xorg method doesn't work in Hardy... :(

[http://ubuntuforums.org/showthread.php?t=929963](http://ubuntuforums.org/showthread.php?t=929963)

---

