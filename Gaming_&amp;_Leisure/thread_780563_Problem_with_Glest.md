---
title: "Problem with Glest"
date: 2008-05-03
forum: Gaming &amp; Leisure
---

### Post by Hamstermerc on 2008-05-03
My problem is that that when i run Glest from either terminal or the applications window it opens for about a second in a new window then that window closes. I tried re-installing and such but nothing worked. 
I used "sudo apt-get install glest" in terminal (new linux user so i hope thats right) if that helps. I don't if its to do with my hardware but other games work fine. 

Any help on the matter would be much apprecited. And on another note is it an alright game? :)

Hamstermerc

P.s. I'm running Ubuntu Hardy Heron distro if that helps

---

### Post by Hamstermerc on 2008-05-07
When i run it in terminal i get this (see attached image). The program opens momentarily and then closes. 

I'm dying to try out this game any help would be much appreciated

---

### Post by atomkarinca on 2008-05-07
I guess the one in the repos is outdated. You should try [these deb packages]("http://getdeb.net/search.php?keywords=glest").

---

### Post by Skatertjah on 2008-05-07
I had the same problems with other programs.
It's probably because another program is using ALSA which stands for The Advanced Linux Sound Architecture. Try closing down any programs that might be using this program (like music or video player and other games) and try running the game again. I might be wrong here. If it doesn't work I don't really know what's going on.
Have a shot at it,
Good luck;)

---

### Post by Hamstermerc on 2008-05-08
> **Skatertjah said:**
> I had the same problems with other programs.
It's probably because another program is using ALSA which stands for The Advanced Linux Sound Architecture. Try closing down any programs that might be using this program (like music or video player and other games) and try running the game again. I might be wrong here. If it doesn't work I don't really know what's going on.
Have a shot at it,
Good luck;)

Thanks i closed rhythmbox and tried opening and it did indeed work :) Pretty alright game as well. Does anyone know a way of letting both work cos id love to have my own music playing in the background.

---

### Post by atomkarinca on 2008-05-08
I can get sounds with mpd+sonata instead of rhythmbox.

---

### Post by mitza on 2008-05-08
didn't want to open a new thread but i also have a problem with glest, i can't run it fullscreen, every time i enter the game it starts in window mode. :( I installed it from getdeb.

---

### Post by atomkarinca on 2008-05-09
Try hitting alt+enter while in the game. Sometimes this doesn't work, if so change the resolution of the game. Open glest.ini with root previliges: in a terminal (Applications > Accessories > Terminal) type:

```
gksudo gedit /usr/local/games/glest/glest.ini
```

Find the lines that say "ScreenHeight" and "ScreenWidth", change them to something smaller than your screen resolution, save, exit and restart the game.

---

### Post by elmaster84 on 2008-05-09
I know that your problem is not the same as mine... but Every time I play the game...after 15 to 20 min...it crashes!!!...ALWAYS...no exception..so Im wondering if anyone has any idea of why this happens

---

### Post by atomkarinca on 2008-05-09
> **elmaster84 said:**
> I know that your problem is not the same as mine... but Every time I play the game...after 15 to 20 min...it crashes!!!...ALWAYS...no exception..so Im wondering if anyone has any idea of why this happens

If you run the game from a terminal then you can see the error it gives when it crashes. Next time you play Glest, open up a terminal (Applications > Accessories > Terminal) and type:

```
glest
```

---

### Post by mitza on 2008-05-09
tanks atomkarinca , you'r solution worked! :KS

---

### Post by atomkarinca on 2008-05-10
> **mitza said:**
> tanks atomkarinca , you'r solution worked! :KS

No problem.

---

### Post by Gouki on 2008-06-27
Weird, I can't find glest.ini in my system. Any idea?

---

### Post by atomkarinca on 2008-06-28
You can create one under ~/.glest folder. Here's mine, you can change it to suit your configuration:

```
 ; === Properties File === 

AiLog=0
AiRedir=0
CheckGlCaps=1
ColorBits=24
ConsoleMaxLines=10
ConsoleTimeout=1
DayTime=1000
DebugMode=0
DepthBits=24
FactoryGraphics=OpenGL
FactorySound=OpenAL
FastSpeedLoops=2
Filter=Bilinear
FilterMaxAnisotropy=1
FirstTime=0
FocusArrows=1
FogOfWarSmoothing=1
FogOfWarSmoothingFrameSkip=3
FontConsole=-*-fixed-*-*-*-*-12-*-*-*-*-*-*-*
FontDisplay=-*-fixed-*-*-*-*-12-*-*-*-*-*-*-*
FontMenu=-*-fixed-*-*-*-*-12-*-*-*-*-*-*-*
Lang=english.lng
MaxLights=1
NetworkConsistencyChecks=1
PhotoMode=0
Platform=Linux
RefreshFrequency=75
ScreenHeight=768
ScreenWidth=1024
ServerIp=192.168.1.102
ServerPort=6666
ShadowAlpha=0.1
ShadowFrameSkip=2
ShadowTextureSize=256
Shadows=Projected
SoundStaticBuffers=16
SoundStreamingBuffers=4
SoundVolumeAmbient=80
SoundVolumeFx=80
SoundVolumeMusic=90
StencilBits=0
Textures3D=1
Windowed=0
```

---

### Post by Zorgoth on 2008-09-07
Responding to the original poster, I have the same problem running it in 64-bit Ubuntu, but in 32-bit it sort of works (I say sort of because I can't get it fullscreen (I'll try the solution posted here) and it keeps crashing after a few minutes.

---

