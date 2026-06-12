---
title: "wow on wine 0.9.23 (SO CLOSE!)"
date: 2006-10-25
forum: Gaming &amp; Leisure
---

### Post by T3h_Dohtem on 2006-10-25
My setup:

ATI X300 128MB
wine 0.9.23 (unpatched)
wow latest patch

I have done the ATI Ubuntu driver install from the guide and that JUST about has me playing. Now when I start wow (in d3d mode, open GL just shows odd shapes and then crashes before I get ingame), instead of crashing before i startup, I can actually get into the game for about 10 seconds, but after that I lock up and have to do a hard shutdown. glxgears runs fine for me, but when I get into WoW, my screen is misaligned. Its as if the whole animated part of the screen has been scrolled down. The top half of my screen is black(blank) and i can see what SHOULD be the top half at the bottom. All the GUI buttons/bars/bells/whistles are where they should be, but the graphics are placed wrong. I have a screenshot if this description is inadequite, just dont know where to host it atm. If anyone can help me it'd be much appreciated.

Dohtem

---

### Post by at0mic on 2006-10-25
ati and linux dont mix well. dont expect miracles, especially in wine

---

### Post by Ferrat on 2006-10-25
> **at0mic said:**
> ati and linux dont mix well. dont expect miracles, especially in wine

That's just ignorence talking nof. 

If you can't run OpenGl the something it wrong with you driver, WoW istallation or your wine installation, In running WoW on Wine 0.9.23 works fine with good FPS 

EDIT: just read you use the Ubuntu ATI driver you need to get the Proprietary Drivers from ATi 
[https://support.ati.com/ics/support/KBAnswer.asp?questionID=1176](https://support.ati.com/ics/support/KBAnswer.asp?questionID=1176)

---

### Post by T3h_Dohtem on 2006-10-26
> **Ferrat said:**
> That's just ignorence talking nof. 

If you can't run OpenGl the something it wrong with you driver, WoW istallation or your wine installation, In running WoW on Wine 0.9.23 works fine with good FPS 

EDIT: just read you use the Ubuntu ATI driver you need to get the Proprietary Drivers from ATi 
[https://support.ati.com/ics/support/KBAnswer.asp?questionID=1176](https://support.ati.com/ics/support/KBAnswer.asp?questionID=1176)
I tried the ATI drivers and I couldnt get ANYTHING to work, it would crash out as soon as I launched WoW, in opengl it would say something about not being able start 3d rendering, in -d3d it would just crash and go to bug report tool. Since I have posted, i have done a complete reformat (edit: repartition/format and reinstall Ubuntu) and reinstalled the ATI drivers from method 2 here ->
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)
Installed the wine dependencies and compiled and installed wine 0.9.23, and reinstalled and patched WoW, and Im still getting the same problem, the login screen is only displaying the top half while the bottom half is below view of the monitor(and the top half is blank). Finishing the last patch now, maybe some miracle will occur. I'll give opengl another shot now too. At least this time the webpage on the patcher shows up correctly.

Thanks again for any suggestions :(

---

### Post by T3h_Dohtem on 2006-10-26
Last patch completed. d3d I get the same problem, half the screen, I just noticed a flicker in the bottom right, then after about 10 seconds, crash. The other odd thing I just noticed this time, is when it went to automatically select my realm, the same background (The doorway with the animated swirl) showed up perfectly. The same thing when it went tot he background of downloading updates, but the login, character selection, and ingame are all messed up.
Opengl never made it to the login screen with a crash and bug report tool loading.
Error message:
---
This application has encountered a critical error:

ERROR #132 (0x85100084) Fatal Exception
Program: C:\WoW\WoW.exe
Exception: 0xC0000005 (ACCESS_VIOLATION) at 0073:7DCECDA0

The instruction at "0x7dCECDA0" referenced memory at "0x00007584" The meory could not be "read"

Press OK to terminate the application.
---

As I write this, the WoW music taunts me in the background :( Somebody please help :*( lol
Thanks again

---

### Post by T3h_Dohtem on 2006-10-27
I tried using the trial of the wine commercial front program Crossover office, and the screen bug doesnt show up...but I still crash :(

Just did an edgy install and updated my ATI drivers, compiling wine 0.9.23 now, I guess we will see what happens :/

If anyone has any other ideas...maybe im missing something here? ](*,) 

Thanks

---

### Post by inthepit on 2006-10-27
i know how you feel.  i cant get WoW to run on wine or the crossover beta with my ati x800.  i get a box that fills about 1/2 my screen and the actual game graphics are all scrunched up to the bottom 1/5 of that box.  but the games text is in the right spots.  I can't seem to find a solution to my problem.  hopefully you can find one for yours and it will help me find mine.  hopefully your upgrade to edgy goes great and you can get it to run.

---

### Post by T3h_Dohtem on 2006-10-29
> **inthepit said:**
> 
hopefully your upgrade to edgy goes great and you can get it to run.


Yeah...not so much.
Upgraded to Edgy and wine wont even compile anymore. Get segfaults (searching the web has found several other people having the same problem) Tried a few fixes for that, nothing giving. Same thing with the new Wine. 0.9.24. On top of that, bluetooth seems to be having some issues with Ubuntu as well. I have to say, things arent going so well for me with this distro lately :(

---

