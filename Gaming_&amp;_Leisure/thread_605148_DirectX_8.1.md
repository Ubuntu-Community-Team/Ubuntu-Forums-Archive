---
title: "DirectX 8.1"
date: 2007-11-06
forum: Gaming &amp; Leisure
---

### Post by Dapman01 on 2007-11-06
Whenever I try to play Half life 2 it says that I have direct X 8.1 when I have an 7800GT which is Direct X 9.0
Is there any way to fix this

---

### Post by Ferrat on 2007-11-06
what version of wine are you using?

sure you don't have a -dx8 tag on a shortcut or something?

---

### Post by Dapman01 on 2007-11-06
> **Ferrat said:**
> what version of wine are you using?

sure you don't have a -dx8 tag on a shortcut or something?

I'm using 0.9.46 
I don't know what you mean by -dx8 tag on a shortcut

---

### Post by cogadh on 2007-11-06
Launch the game like this:
```
wine steam.exe -applaunch 220 -dxlevel 90
```
That will force DX9.

---

### Post by Dapman01 on 2007-11-06
> **cogadh said:**
> Launch the game like this:
```
wine steam.exe -applaunch 220 -dxlevel 90
```
That will force DX9.

patrick@patrick-desktop:~$ wine steam.exe -applaunch 220 -dxlevel 90
wine: could not load L"c:\\windows\\system32\\steam.exe": Module not found
patrick@patrick-desktop:~$ 

that is what I got.  I do have steam installed and half life 2 installed and running, just no directX 9

I think that I failed to mention that the software level direct X 9 is being displayed, but not the hardware level

---

### Post by disturbedite on 2007-11-07
you didn't happen to mess with any of wine's dll files did you?

---

### Post by cogadh on 2007-11-07
> **Dapman01 said:**
> patrick@patrick-desktop:~$ wine steam.exe -applaunch 220 -dxlevel 90
wine: could not load L"c:\\windows\\system32\\steam.exe": Module not found
patrick@patrick-desktop:~$ 

that is what I got.  I do have steam installed and half life 2 installed and running, just no directX 9

I think that I failed to mention that the software level direct X 9 is being displayed, but not the hardware level
You need to change directories to Steam's install directory before running that. Also, I believe the steam executable starts with a capital "S":
```
cd ~/.wine/drive_c/Program\ Files/Steam
wine Steam.exe -applaunch 220 -dxlevel 90
```
Once this command works, the hardware level should report as DX 9, as well as the software level.

---

### Post by Rhubarb on 2007-11-07
Dapman01 you need to change the current directory to where Steam is kept.
To do this you'd have to do something like:
```
cd .wine/drive_c/Program\ Files/Steam/
wine steam.exe -applaunch 220 -dxlevel 90
```

---

### Post by Dapman01 on 2007-11-07
> **cogadh said:**
> You need to change directories to Steam's install directory before running that. Also, I believe the steam executable starts with a capital "S":
```
cd ~/.wine/drive_c/Program\ Files/Steam
wine Steam.exe -applaunch 220 -dxlevel 90
```
Once this command works, the hardware level should report as DX 9, as well as the software level.

That worked beautifully, Now how do I get it to work with my other steam games like Episode 1 and 2, etc

Oh and thanks BTW

---

### Post by Rhubarb on 2007-11-07
I don't run Steam here, so I wouldn't know.
(I run only open source games here)

---

### Post by bastiegast on 2007-11-07
Type Alt-F2, enter regedit and press enter. Go to HKEY_CURRENT_USER > Software > Wine > Direct3D (if its not already there make a new key) Add a new String value: "UseGLSL" and give it the value enabled. This will make your source games detect dxlevel 9.0 It won't add anything to your playing experience though. The only effect it adds is HDR afaik. For me HDR glitches in wine. It's like the lights keeps turning bright and dark. For me anyway.

---

### Post by Dapman01 on 2007-11-07
Oh, ok, thanks
does anyone else know what to put in so that I can use Direct X 9 in my other steam games

---

### Post by Dapman01 on 2007-11-07
> **bastiegast said:**
> Type Alt-F2, enter regedit and press enter. Go to HKEY_CURRENT_USER > Software > Wine > Direct3D (if its not already there make a new key) Add a new String value: "UseGLSL" and give it the value enabled. This will make your source games detect dxlevel 9.0 It won't add anything to your playing experience though. The only effect it adds is HDR afaik. For me HDR glitches in wine. It's like the lights keeps turning bright and dark. For me anyway.

How do I enable the value

---

### Post by Ferrat on 2007-11-07
> **Dapman01 said:**
> How do I enable the value

just add the value as a sting the type enabled in the little box :)

---

### Post by Dapman01 on 2007-11-07
Hmmm...that didn't work, was I suppose to get rid of (Default) if so, it won't let me

(Default)          REG_SZ           (value not set)
Use GLSL        REG_SZ            enable

that is what is up

---

### Post by karth on 2007-11-07
You can leave the default value, it's there, err... by default :p

The correct value to enter is:

```
UseGLSL REG_SZ enabled
```

No space in UseGLSL
And enabled with a **d**

:)

---

### Post by cogadh on 2007-11-07
> **Dapman01 said:**
> That worked beautifully, Now how do I get it to work with my other steam games like Episode 1 and 2, etc

Oh and thanks BTW
Change the applaunch number to whatever game ID belongs to the game you want to run:
220 - Half-Life 2
240 - Counter Strike: Source
280 - Half-Life: Source
300 - Day of Defeat: Source
320 - HL2 Deathmatch
340 - HL2 Lost Coast
360 - HL Deathmatch: Source
380 - HL2 Episode 1
400 - Portal
420 - HL2 Episode 2
440 - Team Fortress 2

If you have any other non-Source, non-Valve or non-English games, they each have their own applaunch number. A complete list of them can be found here:
[http://developer.valvesoftware.com/wiki/Steam_Application_IDs](http://developer.valvesoftware.com/wiki/Steam_Application_IDs)

---

### Post by drzero1 on 2007-11-10
In the steam game list. Right click on a game you want to edit. Click on "set launch options", and add the parameter "-dxlevel 90". Seems to work in that way. But I could be wrong.

---

