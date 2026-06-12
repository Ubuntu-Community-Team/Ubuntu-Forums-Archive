---
title: "age of empires II"
date: 2007-02-10
forum: Gaming &amp; Leisure
---

### Post by linex on 2007-02-10
hi
i got wine installed
i'm new to wine and have no clue how to use it

i want to install age of empires II with wine. i have the original cd how do install it? i know it works because of [http://appdb.winehq.org/appview.php?iVersionId=147](http://appdb.winehq.org/appview.php?iVersionId=147)

thanks

---

### Post by public_void on 2007-02-12
I'd first read the wine and winecfg manuals.
```
man wine
man winecfg
```

To run the setup do
```
wine /media/cdrom/aoesetup.exe
```
This will go through the install as normal. And will be installed in /home/[username]/.wine/drive_c/Program Files/Microsoft Games/Age of Empires II/. To install the expansion pack, run the setup from the expansion pack CD (I'm not sure amount using the AOK gold edition, as both AOK and the expansion are on the same CD). To run change directory to age2_x1(this is the expansion pack, I'm can't remember the directory for AOK, it should be similar), and run the executable in there. I think it should be the same name as the directory.

Your may find AOK doesn't run that well. So you need to tweak some settings using winecfg. 
```
winecfg
```
There is a lot you can change here and settings may vary for each computer, so experiment to find the right settings. Also note a document in the AOK directory called Readme.rtf (Readmex.rtf for expansion). It has know problems and a list of command arguments for the AOK executable. When I installed AOK, the mouse cursor flashed and mouse actions lagged, I found using the argument "NormalMouse" fixed that, resulting in smoother gameplay. 

I've missed quiet a bit, but I hope this helps.

---

### Post by linex on 2007-02-12
thanks
i have the game installed and the no cd patch applied.
the problem occurs when i try to boot the game, i get an error telling me that there was a problem with graphics system. i insert the cd and go to setup again, and click play game. this boots up the game but it lags alot. 

after doing winecft, where did u put in normalmouse?
what other settings did you change, i've not applied the no cd patch

---

### Post by public_void on 2007-02-13
The "NormalMouse" is an argument for the AOK executable, like the arguments you use in the terminal. i.e.
```
wine age2x_1.exe NormalMouse
```
This should give you the standard mouse, which for me reduced lagging. 

I have AOK added as an application in the "Applications" tab, and "Windows Version" as 98. Whilst selecting that I tried different settings, for example setting Direct3D in the "Graphics" tab as "Emulated" then trying "Hardware" to see which worked best. I generally tested the different options depending on what issues I was having.

---

