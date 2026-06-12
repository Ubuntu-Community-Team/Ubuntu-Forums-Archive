---
title: "Okay guys bad ubuntu nvidia bug!!! PLEASE HELP!"
date: 2009-03-15
forum: General Help
---

### Post by rubendodge on 2009-03-15
Okay I have tried everything I could come up with or find on google to fix this problem. No matter what I do I cant so I am officially asking for help. This has been a problem for over 2 months now and I have tried EVERYTHING I could. The problem is as follows.

Problem:
Okay well I have tried to install the nvidia driver through the manual install(already have all required files source,gcc,etc) anyways I also tried to use envy and envyng all of those failed. I have tried to use ubuntu's updater itself to install them and it failed. All I get when it is installed is a black screen and the console window. I removed all nvidia drivers then tried a clean install and that didnt work either. The only thing I havent tried is removing the ubuntu restricted modules which are used for partial video support. I was afraid to because its my only fall back to go to when I remove nvidia. I dont have any other problems than that. Here is my system info.

Operating Systems:
Windows Xp 32 bit
Linux Suse 11.0 64bit
Ubuntu 8.10 32bit

CPU:AMD 64 x2 5400+ dual core at 2.65 GHZ
RAM:Kingston 1gb x2 ram
HARDDRIVE:Maxtor 200gb hardrive
FANS:6 fans
VIDEO CARDS:Geforce 7900 GS x2 on sli

---

### Post by rubendodge on 2009-03-15
Okay I come bearing logs and more logs I hope this helps you guys diagnose the problem.

---

### Post by flugh on 2009-03-15
It may be helpful to also attach your Xorg.0.log so we can see the errors occuring during X's startup. From the nVidia build log, all seems to have worked as intended.

---

### Post by rubendodge on 2009-03-15
Well Ill get that in a a couple of hours when I get back but heres my kernel log aswell so this should give you guys more info on this.

---

### Post by rubendodge on 2009-03-15
Okay sorry for the double post but I uploaded the xorg.0.log file its basicly looks like there is 2 problems. Firstly the 2 video cards are both detected as possible primary devices and neither one is chosen so there is no devices chosen to be used for the x server so then it crashes with no screens found. I hope this will help you find a solution. Tnx in advance.

---

### Post by rubendodge on 2009-03-15
Omg i figured it out from some previous tech support online!!!

[http://ubuntuforums.org/showpost.php?p=6357669&postcount=23](http://ubuntuforums.org/showpost.php?p=6357669&postcount=23)

The solution was having to do with hardware and im not a hardware guy im software so i missed it lol.

---

