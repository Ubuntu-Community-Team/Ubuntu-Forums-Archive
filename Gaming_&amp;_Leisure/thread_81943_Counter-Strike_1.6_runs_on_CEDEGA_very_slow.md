---
title: "Counter-Strike 1.6 runs on CEDEGA very slow"
date: 2005-10-25
forum: Gaming &amp; Leisure
---

### Post by rado_london on 2005-10-25
Hi all
I just installed my fisrt game under linux using CEDEGA.I chose Counter-Strike because it is esay for installing and doesnt require much resources.Unfortunately it runs horably slow.I am using HP Pavilion dv4145ea notebook,1.7Ghz Intel Pentium M,512 MB RAM, and think it is shared graphics.
Do you have any idea about my problem-is ot because of some drivers or something else?
Thanks in advance

---

### Post by souled on 2005-10-25
I installed it without a hitch. Gameplay is fine I suppose... but every so often I get a little freeze of lag. 

Is your 3D acceleration enabled?

---

### Post by seethru on 2005-10-25
what exact video card do you have?

---

### Post by souled on 2005-10-25
Maybe by shared graphics he means onboard?

---

### Post by frodon on 2005-10-26
Don't forget to add the -opengl option when you run cedega, it force the games to use openGL which is native in linux, so you will have less lags.
You can't force all the game to use openGL but i advice you to force openGL on all the games you can.
Run the game with a command like that : ```
sudo cedega CStrike.exe -opengl
```Sorry if you already know that.

---

### Post by ramba on 2005-10-26
I'm having same problems despite I got all the drivers working etc. My TFT is working fine and CS:source seems to run fine, as good as in windows but 1.6 just won't work right. Then I remembered that I had exactly same problems when I used windows 2000: CS didn't work and all the other games did. When I tried CS in WinME it worked perfectly.

I tried changing winver but that didn't affect the poor fps. Any suggestions?

---

### Post by rado_london on 2005-10-26
I never tried this with opengl I will try it later.
My 3D aceleration is not on because I dont know how to swith it on.Can some one help me?
Also Im not sure about my graphics card,but it is on-borad.Is there any way to see exactly what model it is?
Cheers

---

### Post by frodon on 2005-10-26
If your laptop is a [HP pavillion dv4145EA]("http://h10010.www1.hp.com/wwpc/uk/en/ho/WF06b/21675-38187-38191-38191-38191-12200594-53920989.html") as you said in the first post, you have an intel 900 embedded video card.
So open your xorg.conf file (after doing a backup) : ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo gedit /etc/X11/xorg.conf 
```Then modify the corresponding sections to look like that (text in bold) : ```
Section "Device"
	[B]Identifier	"Intel Corporation Intel Default Card"
	Driver		"i810"[/B]
	BusID		"PCI:0:2:0"
EndSection

Section "Device"
	BoardName	"915 GM"
	BusID		"PCI:0:2:0"
	[B]Driver		"i810"
	Identifier	"Intel Corporation Intel Default Card"
	VendorName	"Intel"[/B]
EndSection
```To test your 3D acceleration run this command : ```
glxgears -printfps
```It will show you your FPS score, try it before and after the modification to see if you have improved your acceleration.

---

### Post by rado_london on 2006-01-17
HI
I tested it but im not sure is the result good or bad.
This is the output before modifying the xorg.xonf file:
```
3543 frames in 5.0 seconds = 708.529 FPS
```

And this is after:
```
1298 frames in 5.0 seconds = 259.580 FPS
3986 frames in 5.0 seconds = 797.023 FPS
```

Is this normal?

---

### Post by byoon on 2006-01-17
First off, you could have run CS 1.6 under Wine 0.9.5 and it actually runs faster than with Cedega.  Cedega, in my opinion, is not worth the money.

Secondly, you can use the following command to renice the wine processes and it should resolve your lagging problems.  You should run this after you start Steam or put it into a script with a "sleep 5" before it so it waits 5 seconds, making sure all the wine processes have started.

renice 19 -p `pgrep wine`

---

### Post by ashmew2 on 2007-02-02
Hi guys  , I have been to many tutorials and out of the mixed tutorials  , ive gotten my CS working in UBuntu better den it works in WIn XP :D I had a cstrike_setup.exe (for 1.6 and no steam) SO what i did was :
1)Use wine to install cstrike
2)used cedega to play the game with the command cedega cstrike.Exe -opengl
And its working fine :D

---

### Post by rado_london on 2007-02-02
> **ashmew2 said:**
> Hi guys  , I have been to many tutorials and out of the mixed tutorials  , ive gotten my CS working in UBuntu better den it works in WIn XP :D I had a cstrike_setup.exe (for 1.6 and no steam) SO what i did was :
1)Use wine to install cstrike
2)used cedega to play the game with the command cedega cstrike.Exe -opengl
And its working fine :D

Cheers man will try that ASAP :)

---

### Post by ashmew2 on 2007-02-08
did it work ? Btw , For your info , the cstrike_setup.exe i have is not legal i think cuz Valve stopped standalone EXE installers after 1.5 and u gotta have steam for 1.6. Well , i DLed it off a p2p neways cuz i cant get original CS in my city :(

---

