---
title: "Rear Projection TV (Older Style) Resolution"
date: 2008-02-19
forum: Desktop Environments
---

### Post by DrewMac on 2008-02-19
I just got Ubuntu 7.10 up and running. I am going to use this computer as a MythTV PVR. However, I am on an older Sony 48" rear projection TV. I am trying to change the resolution so i can see the menu bar but it is already at its highest resolution. Is there any way to fix this?

---

### Post by edward4130 on 2008-02-19
Lots of info on how to do this on here looking under mythtv.  Depending on what your video card is and how you are connecting the TV.  Mine is a Nvidia card and i loaded the Nvidia driver and set my my xorg.config file to display the TV by SVIDEO at 600X800.

Make sure that you copy the xorg.config file before you edit it , if it is set wrong it will fubar everything and you are starting in safe to edit it back.

Try mythbuntu forums, lots more info there.

---

### Post by stevejesus on 2008-02-19
You can output (i think) a maximum of 1024 lines over s-video.  If your TV is pre-HD then it will displays images BEST at its native resolution (480i).  So, if the aspect ratio is 4:3 (square) then you will get the best results at 640x480.  If it is 16x9 then you'll want 720x480.

---

### Post by edward4130 on 2008-02-19
Here is a good thread with the NVIDIA information and how to edit the xorg.conf file.

[http://ubuntuforums.org/showthread.php?t=663636&highlight=mythbuntu+xorg.conf]("http://ubuntuforums.org/showthread.php?t=663636&highlight=mythbuntu+xorg.conf")

In the instructions it tells you to copy pase from the working xorg.conf file but you can just cpy the file by going into the directory by:
```
cd /ect/X11/
```

Now List the directory you are in:
```
ls-la
```

copy the xorg file to a backup version you can later replace if you jack it up :) I did several times!!
```
cp xorg.conf xorg.bkp
```

Hope the extra hint helps to keep you from a big rework.

-Edward4130

---

### Post by DrewMac on 2008-02-20
OK thanks. I'll try those suggestions. I have to reinstall Ubuntu anyway as I messed up my MythTV install. I'll try the resolution settings before i wipe the drive, so I don't have much to worry about :P

---

