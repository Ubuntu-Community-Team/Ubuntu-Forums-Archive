---
title: "Video tearing with Compiz &amp; nVidia FIX"
date: 2009-01-06
forum: General Help
---

### Post by psychok9 on 2009-01-06
For many years, I had video tearing problem with all videos and Compiz/effects enabled.
Yesterday I've fixed with this "pass":
1) Sync to VBlank enabled on "OpenGL settings" and X Server XVideo settings.
2) Downloaded from "deb [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) intrepid main #Compiz Fusion" last updates.
3) Open CompizConfig (downloaded from Synaptic) -> General -> General Options > Display Settings tab -> Refreshrate changed from 50 to 60Hz and Sync to VBlank enabled.
4) On "session" (application loaded on boot up of gnome interface), I've added a new command: "nvidia-settings -l".

Now World of Warcraft, Videos and all seem to be with Vsync ON.

I hope it's an good help/fix for all :P

**This is my system spec:**
Ubuntu 8.10 x86_64/amd64, nVidia 8800 GT, nVidia driver 177.80, LCD LG L204WT 60Hz, 2.6.27-9-generic kernel.

---

### Post by mac21 on 2009-01-11
hi, i currently have the video tearing problem and was hoping you could explain step 2 in a little more detail (im knew to linux)

thanks

---

### Post by psychok9 on 2009-01-11
> **mac21 said:**
> hi, i currently have the video tearing problem and was hoping you could explain step 2 in a little more detail (im knew to linux)

thanks

I have the Italian version of Ubuntu, so the menu is different from the English version.
Anyway, firstly, you can try to verify if the "VBlank" is enabled on "OpenGL settings" and "X Server XVideo settings". You can see it on the "NVIDIA X Server settings" that you can find on menu System -> Administration -> NVIDIA X Server settings.
Secondly, you can try to insert on System -> Preferences -> Sessions -> Start programs -> Add -> on command field: nvidia-settings -l (without any comma), on name field: Nvidia load.
Thirdly, download CompizConfig from Synaptic "compizconfig-settings-manager", that you can find (after installing) on System -> Preferences -> CompizConfig, and go to General options -> Display settings -> Refreshrate, and write 60 (if you have a LCD monitor), and check Sync to VBlank on right box.

---

