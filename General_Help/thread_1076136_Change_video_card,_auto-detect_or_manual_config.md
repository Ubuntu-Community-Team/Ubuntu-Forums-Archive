---
title: "Change video card, auto-detect or manual config?"
date: 2009-02-21
forum: General Help
---

### Post by UranUtan on 2009-02-21
Hi,

My computer has an integrated video chip (Intel 865G), I set in the BIOS that this video card use 32MB shared memory (the max value). I think it has some problem as each time I log in, the resolution becomes lower and the display becomes unknown. As a consequence, the list of selectable resolutions is very few.

At each reboot, I have to go to Screen Resolution utility. Hit 2 or 3 times on the "Detect Display" button until the monitor is recognized. Then I can change the resolution.

I have no idea what is wrong. May be I have messed up with gnome config (.gconf and .gnome2 were deleted after I got graphics issues trying playing Windows games under Wine: [http://ubuntuforums.org/showthread.php?t=1062501](http://ubuntuforums.org/showthread.php?t=1062501))

At any rate, may be the integrated video chip is not good enough or may be 32 MB video RAM is not enough. I am going to change for a better video card. I would like to know what would happen when Ubuntu starts and suddenly it finds a completely different video card.

Would Ubuntu auto-detect and auto-configure the graphics settings or should I do some manual configuration? If manual config is needed, what should I do?

Thanks in advance for any help.

---

### Post by UranUtan on 2009-02-21
Hi,

Just got an used Sapphire ATI Radeon 9250 128 MB. I followed the instructions here [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

All the checkings for the closed source ATI driver "fglrx" were negative because my video was integrated Intel 865G. The only thing I did was:
```
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri
```
I skipped the manual edit of xorg.conf. Just made a backup of that file. Then I shut down the computer. BIOS setup: disabled the integrated video and activated the AGP ATI Radeon 9250 card. Then rebooted.

I expected graphics troubles and was worried to go through a lot of manual config that I know nothing about.

Fortunately, the login screen came up, I could log in and everything is magically recognized: monitor, various screen resolutions, even the refresh rate has several choices instead of 60Hz as before (I used CRT monitor). I have no idea how Ubuntu picked up all of these settings by itself but it was a big relief.

---

