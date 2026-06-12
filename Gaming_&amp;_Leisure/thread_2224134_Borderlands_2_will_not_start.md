---
title: "Borderlands 2 will not start"
date: 2014-05-14
forum: Gaming &amp; Leisure
---

### Post by mrslig100 on 2014-05-14
Hi ubuntu forums :)
This is my first post so if I do somthing wrong let me know :P
I have spent my whole life using windows and have recently moved over to ubuntu as my first proper linux OS.
Needless to say it is an absolutley fantastic OS and I have no intentions of returning to windows.
So far ive only got apps such as Photoshop CS4 going along with various portable app versions.
However I have hit a dead end trying to get a non steam copy of borderlands 2 going.
I started a game with a relative which we had to leave for reasons which we plan on finishing.
It would be sad if we dont.
The problem is quite simply getting the game to launch.
It wont simple as that even with the windows 8 launcher "fix".

All the best. Hope you can help.

---

### Post by T.J. on 2014-05-15
Am I correct in assuming that Borderlands 2 is a Windows game that you are trying to run with WINE?

---

### Post by mrslig100 on 2014-05-15
Thats right.
Ive tried configuring DLL's installing redistributables the usual bla bla bla.
But it simply refuses to start!

---

### Post by oldrocker99 on 2014-05-15
The game does have a Gold rating on the Wine app database; it is the Steam version reported on. What happens if you run the game from a terminal?

```
wine (nameofprogram).exe
```

---

### Post by T.J. on 2014-05-16
Wine will never be completely compatible.  That said, in order to have a chance at helping you:

Which version of Wine are you using?
Which version of Linux?
Are you using Winetricks?

Just because a game has a "gold" rating does not mean it will work out of the box, or even at all.  I just means someone got it working and sent in a gold rating.  By far the best way to get games working is to use Xen or KVM  with VGA passthrough.

---

### Post by mrslig100 on 2014-05-16
Im well aware that it even gold rated apps wont just work simple as that. 
And 1 rating can be very different from another depending on plugins/distros/users ect.
Ive tried starting it from the terminal but still no result.

Im on wine 1.6.2
Ubuntu 14.04
And yes I am using winetricks.

---

### Post by Peter_Solver on 2014-05-17
[COLOR=#3F4549][FONT=Helvetica Neue]Borderlands 2 is an old game. I don't know if it's wise to invest money on porting something to Linux that majority of people wanted to play.[/FONT][/COLOR]

---

### Post by oldrocker99 on 2014-05-17
> **Peter_Solver said:**
> [COLOR=#3F4549][FONT=Helvetica Neue]Borderlands 2 is an old game. I don't know if it's wise to invest money on porting something to Linux that majority of people wanted to play.[/FONT][/COLOR]

Uh, it came out in 2012 (old?), it's still widely played, and if if a majority of people want to play it, and there are over 900K Linux users on Steam, it would follow that it IS worth the money to port it.

---

### Post by mrslig100 on 2014-05-17
This is not a steam copy and I will be playing it over VPN.
Why would I have to invest cash in porting it?

---

### Post by T.J. on 2014-05-17
> **mrslig100 said:**
> Im well aware that it even gold rated apps wont just work simple as that. 
And 1 rating can be very different from another depending on plugins/distros/users ect.
Ive tried starting it from the terminal but still no result.

Im on wine 1.6.2
Ubuntu 14.04
And yes I am using winetricks.

Super!  Would you please copy and paste the results from your terminal, if possible?

---

### Post by mrslig100 on 2014-05-17
'/home/slig/.PlayOnLinux/wineprefix/Borderlands/drive_c/Program Files (x86)/2K Games/Borderlands 2/Binaries/Win32/Borderlands2.exe' 
err:module:import_dll Library Steamclient.dll (which is needed by L"Z:\\home\\slig\\.PlayOnLinux\\wineprefix\\Borderlands\\drive_c\\Program Files (x86)\\2K Games\\Borderlands 2\\Binaries\\Win32\\steam_api.dll") not found
err:module:import_dll Library buddha.dll (which is needed by L"Z:\\home\\slig\\.PlayOnLinux\\wineprefix\\Borderlands\\drive_c\\Program Files (x86)\\2K Games\\Borderlands 2\\Binaries\\Win32\\steam_api.dll") not found
err:module:import_dll Library steam_api.dll (which is needed by L"Z:\\home\\slig\\.PlayOnLinux\\wineprefix\\Borderlands\\drive_c\\Program Files (x86)\\2K Games\\Borderlands 2\\Binaries\\Win32\\Borderlands2.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"Z:\\home\\slig\\.PlayOnLinux\\wineprefix\\Borderlands\\drive_c\\Program Files (x86)\\2K Games\\Borderlands 2\\Binaries\\Win32\\Borderlands2.exe" failed, status c0000135
slig@sligsbeast:~$ 

(also I did the origonal installation as you see in playonlinux as I could not get to the point where the installer extracted the files to on wine)

Hope it helps ;)
So do I need to shove these missing dll's into wines sys32 or the application directory, configure them in winetricks what?

---

### Post by oldrocker99 on 2014-05-18
Putting them in the application directory nearly always works, I have found.

---

### Post by mrslig100 on 2014-05-19
Haha!
Simple as that!
I have got it to start up and as most games do when first run it changes my resolution to a pre configured low resolution however I am not getting any picture rendering. No window or anything.
Is it my directx?
Should I reinstall it?

---

### Post by mrslig100 on 2014-05-20
I have found a solution to this problem based off of a similar problem I found online and messing around in wine
1:
Go into Configure Wine
2:
Select the Graphics tab
3:
Tick "Emulate a virtual desktop"
(Its also advisable to tick Automatically capture the mouse in full-screen windows box)
I hope this information will help anyone else who had this problem and have found this thread on a Google search)

---

