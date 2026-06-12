---
title: "A problem with a gamepad and an old game"
date: 2013-07-01
forum: Gaming &amp; Leisure
---

### Post by bnjrpkr on 2013-07-01
[COLOR=#000000]I'm struggling today. I ordered the PC version of NBA Live 2000 for nostalgia's sake and I also got a Kinobo USB Gamepad. I can't seem to figure out how to install the game using Wine. It installs everything but then it won't run from the shortcut that it creates on the desktop. I haven't figured it out at all yet.[/COLOR]

[COLOR=#000000]The gamepad isn't being recognized at all by Ubuntu. I looked for information online and I installed Joystick and I tried to install jscalibrator as the guides say to do but I'm using Ubuntu 13.04 64 bit and the program is apparently no longer available in the repositories. I'd hate to have just wasted money on both of the items if I can't get them to work. Does anybody have experience with these situations or have ideas to try?[/COLOR]

[COLOR=#000000]Thanks.[/COLOR]

---

### Post by mastablasta on 2013-07-02
i dont' know abotu the gamepad. but you could try to run the game from command line by 

wine game.exe

where game.exe is the game's executable.


then you should see any errors it might give out. also check wine appdb to see if others reported any issues or tips on how ot launch it.

---

### Post by bnjrpkr on 2013-07-02
When I tried to open the game from the command line just now I got the following message:

wine: cannot find L"C\\windows\\system32\\nbawin.exe

---

