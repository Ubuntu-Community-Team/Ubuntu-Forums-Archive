---
title: "True Combat Elite Install"
date: 2012-11-21
forum: Gaming &amp; Leisure
---

### Post by Joon Lee on 2012-11-21
TRYING TO RUN ON WINE (because, for some reason, the windows game works faster on wine than the native linux version does)
I installed Wolfenstein and pasted the cqb folders and patch. The only problem is, I do not know how to create the shortcut to start the game. Here is the info from the README:
/////////////////////////////////////
Initially start TC:CQB like this or use the included autoexec.cfg:

DriveName:\PathToWET\ET.exe +set fs_game cqbtest +set com_soundMegs 64 +set com_hunkMegs 256 +set com_zoneMegs 64 +set s_khz 44 +set r_maxpolyverts 16384 +set r_maxpolys 4096

,e.g.,

"C:\Program Files\Wolfenstein - Enemy Territory\ET.exe" +set fs_game cqbtest +set com_soundMegs 64 +set com_hunkMegs 256 +set com_zoneMegs 64 +set s_khz 44 +set r_maxpolyverts 16384 +set r_maxpolys 4096


Expert users might alternatively change their profile (etconfig.cfg) accordingly
////////////////////////////////////

can someone tell me how to create the aforementioned shortcut?

!!!!!!!!!UPDATE!!!!!!!!!!!!!!!!
I windows installed True Combat: Elite through wine.  Afterward, there were shortcuts on my desktop that would run True  Combat: Elite. I opened up that shortcut (whose name was  "tcetest.desktop"), renamed it "cqbtest.desktop", and opened it up in a  text editor. Following the syntax used in this shortcut, I copied in the  text from the readme and modified it to fit the syntax the shortcut was  using. I hope it works and will get back to the community on this soon.
!!!!!!!!UPDATE!!!!!!!!!!!!
The CQB Community is dead, so I play Elite now.

---

### Post by Joon Lee on 2012-11-21
See update above

---

### Post by holastickboy on 2012-11-22
> **Joon Lee said:**
> TRYING TO RUN ON WINE (because, for some reason, the windows game works faster on wine than the native linux version does)
I installed Wolfenstein and pasted the cqb folders and patch. The only problem is, I do not know how to create the shortcut to start the game. Here is the info from the README:
/////////////////////////////////////
Initially start TC:CQB like this or use the included autoexec.cfg:

DriveName:\PathToWET\ET.exe +set fs_game cqbtest +set com_soundMegs 64 +set com_hunkMegs 256 +set com_zoneMegs 64 +set s_khz 44 +set r_maxpolyverts 16384 +set r_maxpolys 4096

,e.g.,

"C:\Program Files\Wolfenstein - Enemy Territory\ET.exe" +set fs_game cqbtest +set com_soundMegs 64 +set com_hunkMegs 256 +set com_zoneMegs 64 +set s_khz 44 +set r_maxpolyverts 16384 +set r_maxpolys 4096


Expert users might alternatively change their profile (etconfig.cfg) accordingly
////////////////////////////////////

can someone tell me how to create the aforementioned shortcut?

!!!!!!!!!UPDATE!!!!!!!!!!!!!!!!
I windows installed True Combat: Elite through wine.  Afterward, there were shortcuts on my desktop that would run True  Combat: Elite. I opened up that shortcut (whose name was  "tcetest.desktop"), renamed it "cqbtest.desktop", and opened it up in a  text editor. Following the syntax used in this shortcut, I copied in the  text from the readme and modified it to fit the syntax the shortcut was  using. I hope it works and will get back to the community on this soon.

Have you enabled the Playdeb.net repository for your True Combat: Elite installation? It's optimised for Ubuntu, and should get you excellent performance.  

Check out:
[http://www.playdeb.net/software/True%20Combat%20Elite](http://www.playdeb.net/software/True%20Combat%20Elite)

And how to enable the repository:
[http://www.playdeb.net/updates/Ubuntu/12.04#how_to_install](http://www.playdeb.net/updates/Ubuntu/12.04#how_to_install)

---

### Post by Joon Lee on 2012-11-23
I havent, and for now dont feel like reinstalling, but the game runs smoothly anyway so I dont think any more optimization is needed. 

Is there a large amount of optimization done, however? If so, then that would be a great reason for me to reinstall.

---

### Post by holastickboy on 2012-11-25
> **Joon Lee said:**
> I havent, and for now dont feel like reinstalling, but the game runs smoothly anyway so I dont think any more optimization is needed. 

Is there a large amount of optimization done, however? If so, then that would be a great reason for me to reinstall.

It's not huge, but if you were looking for every bit of performance increase, might be nice. Totally should add the PPA for future game installs though, as its updated for more regularly than the vanilla PPAs for games.

---

### Post by Joon Lee on 2012-11-26
Ok. Thanks for the info. I will remember this if I ever get frustrated by performance!

---

