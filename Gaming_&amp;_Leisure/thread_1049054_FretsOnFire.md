---
title: "FretsOnFire"
date: 2009-01-24
forum: Gaming &amp; Leisure
---

### Post by monkeychick on 2009-01-24
Hi,
I just installed frets on fire, and now when I click on the game on the game to play it, it doesn't load, no error messages or anything comes up just nothing changes.

Does anyone know why this is.
Thanks for your help

---

### Post by diwas on 2009-01-24
goto terminal and type:
fretsonfire

and post your output.

---

### Post by monkeychick on 2009-01-24
Hi thanks, here is the output. Its all gobbldygook to me. 



michelle@michelle-desktop:~$ fretsonfire
Traceback (most recent call last):
  File "./FretsOnFire.py", line 64, in <module>
    engine = GameEngine(config)
  File "/usr/share/games/fretsonfire/game/GameEngine.py", line 155, in __init__
    self.video.setMode((width, height), fullscreen = fullscreen, multisamples = multisamples)
  File "/usr/share/games/fretsonfire/game/Video.py", line 68, in setMode
    self.screen = pygame.display.set_mode(resolution, flags)
pygame.error: Couldn't find matching GLX visual
michelle@michelle-desktop:~$

---

### Post by diwas on 2009-01-24
Is your graphics driver properly installed? Is it working properly?

---

### Post by monkeychick on 2009-01-24
I have no idea, could you tell me in baby steps how to find out, I'm not very pc literate, and what I do no I have learnt by trial and error ;) I have been using Linux for about 4 days so its all new to me.
Thank you for your help.

---

### Post by monkeychick on 2009-01-24
*know* ;)

---

### Post by rednano12 on 2009-01-24
Which version of FoF are you using? Where did you download it? The best place to get help would be here: [www.fretsonfire.net](www.fretsonfire.net)

---

### Post by diwas on 2009-01-24
> **magicman692 said:**
> Got it!!!!!

```
sudo gedit /etc/X11/xorg.conf
```

This should open xorg. Next, go to about 40 lines down, and you should see this:

```
Identifier	"Default Screen"
	Device		"Intel Corporation 82865G Integrated Graphics Controller"
	Monitor		"DELL E773c"
	DefaultDepth	16
```

Just change the default depth (in my case, 16, but could be any other number) to 24, restart "X" (or if you dont know how, just restart your computer), and start FoF. It should work, but mine goes pretty slow.

Thanks alot to the guy who found this out! ([http://avokadaro.blogspot.com/2007_09_01_archive.html](http://avokadaro.blogspot.com/2007_09_01_archive.html))

Here's what I've found. 
Could you tell me if ur system is 64bit or 32bit?

---

### Post by monkeychick on 2009-01-25
This is what I get, and Im not sure what bit my machine is. I'll try to find out.


Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

---

### Post by monkeychick on 2009-01-25
@rednano
I installed it using the package manager, I will try that link thanks

---

### Post by diwas on 2009-01-25
> **monkeychick said:**
> This is what I get, and Im not sure what bit my machine is. I'll try to find out.


Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
Umm well...I am sorry, I googled a lot but couldn't find a strong reply. But yeah you should try to install from the direct link provided by the FoF website. It seems like the repo's version is outdated. 
I tried to play this game but i have very small graphics memory, so couldnt...:(

---

### Post by monkeychick on 2009-01-25
Hi.
Thank you very much for trying to help. I'll try the download and if it doesn't work I'll just give up ;)

---

### Post by Flimm on 2009-01-25
Have you installed all the drivers in System, Administration, Hardware Drivers?

---

### Post by monkeychick on 2009-01-27
I followed that and the message said

"No Proprieraty drivers are in use on this system" 

Is that bad?

---

### Post by diwas on 2009-01-28
Which graphics card do u have?

And no..its not bad..hehe. Actually, if u have a proprieraty driver of graphics card like NVIDIA or ATI, you have to install that kind of driver. So there might be two cases..either you dont have those cards or you have one of those cards but the driver is not installed.

---

