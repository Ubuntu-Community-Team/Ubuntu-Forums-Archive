---
title: "HOW-TO Install Diablo LOD 1.11 Patch"
date: 2005-08-01
forum: Gaming &amp; Leisure
---

### Post by KrazyPenguin on 2005-08-01
[B]The NEW patch was just released today.
It won't install automatically with Linux, so you must download the patch first, and then install it.

Here is the How-TO:

44. Download New Patch LODPatch_111.exe from [http://ftp.blizzard.com/pub/diablo2exp/patches/PC/](http://ftp.blizzard.com/pub/diablo2exp/patches/PC/)
45. Place the file, LODPatch_111.exe in your Diablo II directory located at /home/username/.wine/fake_windows/Program Files/Diablo II.
46. Right-click on LODPatch_111.exe and choose “Open with WINE”.
47. The installer will start and then tell you that the patch was installed successfully.
48.The Game will begin.  
49.Have fun again !!!!         ;-)[/B]

**And here is the whole guide for those of you that missed it:**

I made this guide using several sources off the internet and by doing my own experimenting and
I have yet to find a guide on the web with as much detail as the one you are about to read ;-)
Just make sure you don't leave any of the steps out, because leaving out even one step could
cause this installation not to work. 

1.Setup Wine according to Krazypenguin's Wine Setup Guide.
2.Place D2 “Install Disc” in the cdrom drive and mount.
3.Open a terminal and run “wine /pathtocdrom/install.exe” where the /pathtocdrom/ might be /media/cdrom0.  
4.A Diablo II Setup screen appears. Click “Install Diablo II” then click “Full Install”.
5.Agree to the license terms and then enter your name and CD-Key.
6.On the “Choose instal directory” screen pick c: and program files. OK.
7. Desktop Shortcut comes up, and choose No because it won't create the shortcut anyway.
8.When the message comes up *Please Insert the CD labelled Play Disc*, then  eject and put Play Disc in drive.
9.Press Ok.
10.When the message comes up *Please Insert the CD labelled Cinematics Disc*, then  eject and  put Cinematics Disc in drive.
11. Press Ok.
12. When the message comes up *Please Insert the CD labelled Install Disc* again, then eject and put Install Disc in drive.
13. Press Ok.
14. Run Video Test --> Yes (this is actually questionable to run it at this time --- can be ran anytime)
15. If you screen resolution is messed up now, then System -> Preferences -> Screen Resolution and then change your resolution back to the previous setting and apply.
16. View Read Me --> No
17. Register Electronically --> No
18. Play Diablo II screen comes up.  Close the window.
19. Unmount, eject, and place the LOD disc into the drive and mount.
20. Open a terminal and run “wine /pathtocdrom/install.exe” , which is the same command that was executed earlier.
21. Click “Upgrade to Lord Of Destruction”, agree and enter CD-Key, create desktop “NO” .
22. When the message comes up *Please Insert the CD labelled Play Disc*, then  eject and put Play Disc in drive.
23. Press Ok.
24. When the message comes up *Please Insert the CD labelled Expansion Disc*, then eject and put Expansion Disc in drive.
25.Press Ok.
26. View Read Me --> No
27. Register D2 LOD --> No
28. Close the Diablo II LOD window.
29. NoW we need to download a file “LODPatch_110.exe”.  Goto [www.battle.net/files.shtml](www.battle.net/files.shtml) 
30. Scroll down to Diablo II: Lord of Destruction 1.10 Patch and click.
31.Choose under Windows, the Expansion download which is 4.88MB and of course download it.
32. Place the file, LODPatch_110.exe in your Diablo II directory located at /home/username/.wine/fake_windows/Program Files/Diablo II.
33. From Konsole run this command “wine /home/username/.wine/fake*/Pro*/Dia*/LOD*
34. After the Blizzard update says it was successful, press OK and then a message appears “Diablo II was unable to detect a disc in your CD-ROM drive.”  Press cancel.
35. Open /home/username/.wine/config file.
36. Change win98 to nt40 in the # [wineconf] section.  This allows the game to get past the security check.
37. nt40 only allows for 2D gameplay which is fine for this game so open the Diablo II directory again and run the video test file, D2VidTst.exe (located in /home/username/.wine/fake_windows/Program Files/Diablo ii/).  Type in the termianl “wine /home/username/.wine/fake*/Pro*/Dia*/D2V*.
38. If you screen resolution is messed up now, then System -> Preferences -> Screen Resolution and then change your resolution back to the previous setting and apply.
39. To enable sound find this line in your config file under [dsound]
 ;"HardwareAcceleration" = "Emulation" and remove the “;” to enable it.
40. To run the game open a termial to Diablo II directory and type wine Game.exe.
41. To pick up items while holding down the <alt> key, the alt key must be disabled.
Open System -> Preferences -> Windows -> Where it says “Movement Key” switch it form “Alt” to “Super”
42. Have fun ;-)

43. To pick up items using alt-left click you must disable the alt-left click mouse button in KDE:
--> window behaviour - Modifier Key + Left Button --> change to nothing
44. Download New Patch LODPatch_111.exe from [http://ftp.blizzard.com/pub/diablo2exp/patches/PC/](http://ftp.blizzard.com/pub/diablo2exp/patches/PC/)
45. Place the file, LODPatch_111.exe in your Diablo II directory located at /home/username/.wine/fake_windows/Program Files/Diablo II.
46. Right-click on LODPatch_111.exe and choose “Open with WINE”.
47. The installer will start and then tell you that the patch was installed successfully.
48.The Game will begin.  
49.Have fun again !!!!         ;-)

---

