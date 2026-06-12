---
title: "915resolution will not show 9:15 (1280x768) resolutions"
date: 2006-06-19
forum: Desktop Environments
---

### Post by T800vsT1000 on 2006-06-19
Hi Guys,

I have a Dell Dimension 3100 with

0000:00:00.0 Host bridge: Intel Corporation 915G/P/GV/GL/PL/910GL Processor to I/O Controller (rev 04)
0000:00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Express Chipset Family Graphics Controller (rev 04)

I have worked with this PC and Windows XP for a few weeks in resolution 1280x768, because this is the native resolution the monitor.

Because I don't like Windows very much, I'm using dapper 6.06 at the moment. The only problem I have, is that I can't get the resolution at 1280x768.

915resolution gives the following list (see beneath)

Has you can see, these are only 4:3 resolution. I guess 915resolutions looks at my VBT (Video Bios Table). I have updated this table by updating the whole system bios with the newest bios available from Dell. But still no 1280x768. The intel chipset is supporting this resolution I guess, because in Windows it works fine.

Do you guys know, why 915resolution is showing only 4:3 resolutions and more importantly, how can I get it to show the desired 1280x768 resolution. 

From that situation, I can edit xorg.conf to display 1280x768 using the README file from 915resolution.

> Intel 800/900 Series VBIOS Hack : version 0.5.2

Chipset: 915G
BIOS: TYPE 1
Mode Table Offset: $C0000 + $269
Mode Table Entries: 27

Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1920x1440, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1920x1440, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1920x1440, 32 bits/pixel

PS. This is a subpost from [http://www.ubuntuforums.org/showthread.php?t=199398](http://www.ubuntuforums.org/showthread.php?t=199398) (This post title doesn't cover the question anymore)

---

### Post by fast1 on 2006-06-19
Did you try to set a video mode with 915resolution?
You should just pick a mode you don't need (for example, mode 5a 1600x1200) and set it to the new resolution. For example, 

> 915resolution 5a 1280 768

---

