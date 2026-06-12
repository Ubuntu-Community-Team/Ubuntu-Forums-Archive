---
title: "HOMM5 - installation problem"
date: 2006-06-15
forum: Gaming &amp; Leisure
---

### Post by Garyu on 2006-06-15
OK, so I am trying to install Heroes of Might and Magic 5 using Wine (it says on wine homepage it will work with no problems).

I added the wine repository according to instructions on the wine homepage, so my version is 0.9.15 for dapper drake.

Then I insert the HOMM5 dvd and type in a terminal "wine setup.exe" and everything runs smooth until 100% installed on the slider. Then a message box comes up: "Please insert disk 1, containing file "setup.exe". This is required to finish the install". But no matter how I try to point to the DVD it can not find setup.exe... BUT IT IS SETUP.EXE WHO IS ASKING FOR ITSELF!!!!

gah... what is the problem here and how do I solve it? Really frustrating... ](*,)

---

### Post by seth0x2b on 2006-06-15
A quote from [http://appdb.winehq.org/appview.php?versionId=4905](http://appdb.winehq.org/appview.php?versionId=4905) :
> 
[COLOR=Red]# If the setup program asks for 'setup.exe', kill it, and then run 'killall -9 IKernel.exe'[/COLOR]
# Open the file 'video/intro.xml' in the game folder and remove the first two '<Item> . . . </item>' blocks
# Place d3dx9_25.dll in Wine's windows/system32 directory
# This game needs a crack
# If the game does not appear after the loading screen, run 'winecfg', go to the Graphics tab and uncheck the option that allows the window manager to control Wine applications


Cheers

---

