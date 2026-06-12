---
title: "Serious Sam 2 Linux client problems."
date: 2009-03-23
forum: Gaming &amp; Leisure
---

### Post by MaximB on 2009-03-23
Hello !

I've tried to install the game with both Linux Public Beta Clients from here : [http://files.seriouszone.com/catdisplay.php?catid=111](http://files.seriouszone.com/catdisplay.php?catid=111)

I did everything right, but in both client I get those errors :

When running the script :

> ./RunSam2: line 1:  8574 Segmentation fault      ./Bin/Linux-Dynamic-Release/Sam2


When running the bin :

> ./Sam2: error while loading shared libraries: Bin/Linux-Dynamic-Release/Core.so: cannot open shared object file: No such file or directory


I understand that there is no "Final" client and never will be.

How can I run this game natively ?

---

### Post by rizzeh on 2009-03-23
I've just tried Serious Sam 2 native from installer in your post. Got to menu and run through prerecorded demo. All seems fine, apart from no sound, but i've not had a look why yet.

---

### Post by rizzeh on 2009-03-23
screenshot

---

### Post by MaximB on 2009-03-23
Yeah , I believe you that it's working...

I'm just trying to find out why it's not working for me.

I assume it's some problems with the libraries, but I do have the Core.so file and it's linked to /usr/lib/Core.so 

What could be the problem and how do I fix it ? ....

---

### Post by MaximB on 2009-03-24
Alright...
I've tried the Loki installer for SS2 and it did install the game with no problems.
But when I try to run the game it says :

Segmentation fault

Then when I view the log :

[email]maximb@maximb-home:~/maxddark/games/serious.sam[/email]2$ cat Sam2.log 
                 
> 

        -------- START OF LOG --------

LOG:  Core version: $Version: Serious Sam 2; 2.070.00:65824; 2006-PATCH-2-070-inc$
LOG:  Command:  $
LOG:  Initializing timer.
LOG:  Timestamp: 2009/03/24 21:09:45
LOG:  Binary name: Sam2
LOG:  Binary soft path: Bin/Linux-Dynamic-Release/
LOG:  Binary hard path: /home/maximb/maxddark/games/serious.sam2/Bin/Linux-Dynamic-Release/
LOG:  Application directory: /home/maximb/maxddark/games/serious.sam2/
LOG:  Loading group files...
LOG:    All_PC_02.gro: 5213 files
LOG:    Movies_PC_01.gro: 56 files
LOG:    All_PC_01.gro: 1194 files
LOG:    All_PC_03.gro: 3274 files
LOG:    Movies_PC_02.gro: 44 files
LOG:  --- Serious Engine Startup ---
LOG:
LOG:    Type: Unix
LOG:  Detecting CPU...
LOG:  Vendor: GenuineIntel
LOG:    Type: 0, Family: 6, Model: 7, Stepping: 7
LOG:     MMX: Yes
LOG:     SSE: Yes
LOG:    CMOV: Yes
LOG:   Clock: 1466 MHz
LOG:
LOG:  Config file 'Content/SeriousSam2/Config/boot.cfg' doesn't exist.
LOG:  Processing config file 'Content/SeriousSam2/Config/autoexec.cfg'.
LOG:  Processing config file 'Content/SeriousSam2/Config/user.cfg'.
LOG:  Loading cvars from "Content/SeriousSam2/Sam2.ini".
LOG:  Multimonitor is not supported on this platform.


What's the problem and how do I fix it ?

P.S
I have only one monitor.

---

