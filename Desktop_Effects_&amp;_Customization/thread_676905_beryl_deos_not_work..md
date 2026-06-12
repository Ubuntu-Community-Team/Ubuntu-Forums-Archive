---
title: "beryl deos not work."
date: 2008-01-24
forum: Desktop Effects &amp; Customization
---

### Post by Hugh Mulqueen on 2008-01-24
The specs of my laptop are as follows:

Intel Celeron M430 1.73GHz
15.4" widescreen TFT 
512MB DDR2 RAM

Regarding the graphics card this is the output of lspci:
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

and a S-Video Output

I am running linux Mint (A distro thats based on ubuntu)

I installed mint a while ago. Everything worked so i was happy.
Beryl also worked.

I tried to hook my laptop onto a standard def TV.
so i turned down the screen resolution.
When i turned back up the res. and logged back on i lost beryl and everything else
can't play 3D games.:(

If anybody could help that would be great!!!!

---

### Post by overdrank on 2008-01-26
> **Hugh Mulqueen said:**
> The specs of my laptop are as follows:

Intel Celeron M430 1.73GHz
15.4" widescreen TFT 
512MB DDR2 RAM

Regarding the graphics card this is the output of lspci:
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)

and a S-Video Output

I am running linux Mint (A distro thats based on ubuntu)

I installed mint a while ago. Everything worked so i was happy.
Beryl also worked.

I tried to hook my laptop onto a standard def TV.
so i turned down the screen resolution.
When i turned back up the res. and logged back on i lost beryl and everything else
can't play 3D games.:(

If anybody could help that would be great!!!!

HI and you may check your xorg to see what driver is being used because it may have changed and you can try and reconfigure your xorg ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

