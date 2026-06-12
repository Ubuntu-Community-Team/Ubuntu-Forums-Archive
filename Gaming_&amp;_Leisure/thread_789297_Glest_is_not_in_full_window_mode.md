---
title: "Glest is not in full window mode"
date: 2008-05-10
forum: Gaming &amp; Leisure
---

### Post by Taras on 2008-05-10
Hi

Can anyone please help me to enlarge or to make the game in full screen please, in the glest game options there is no  choice of enlarging window area. I have a screen print of my desktop below so that you can see of what  i am a talking about. 

please help me to make the game in full screen please

Thank you

---

### Post by Perfect Storm on 2008-05-10
If I'm not wrong you can do that in glest config file which is placed as hidden in your home directory. You can edit that with a text editor.

---

### Post by Taras on 2008-05-10
Ohh, but i dont know how to edit i dont know programming langvuage

---

### Post by Perfect Storm on 2008-05-10
It's not programming language. It's simple setup option just in text form.

---

### Post by atomkarinca on 2008-05-10
Open up a terminal (Applications > Accessories > Terminal) and type:

```
gksudo gedit /usr/local/games/glest/glest.ini
```

The last line Windowed should be 0. If so then change the resolution. For example normally I use 1024*768 and 800*600 works well for me. The first one goes to ScreenWidth and the second one goes to ScreenHeight, save the file and give it a go.

---

### Post by Taras on 2008-05-10
How can i chnage the resolution 

i dont know what to type in 

what do i type in o and then the number

---

### Post by atomkarinca on 2008-05-10
If you opened the file you should see two lines to the bottom: ScreenWidth and ScreenHeight. For 1024*768 resolution you should change ScreenWidth to 1024 and ScreenHeight to 768. As I mentioned earlier Glest may not work fullscreen for your default resolution. So if your default resolution is i.e. 1024*768 then you should change those numbers to 800 and 600, respectively.

---

### Post by Taras on 2008-05-10
This is what i get when i type your command

---

### Post by Istonian on 2008-05-10
Just hit Alt+Enter while in game.

---

### Post by atomkarinca on 2008-05-10
> **Taras said:**
> This is what i get when i type your command

Then first you should find where glest.ini is located. In the terminal type:

```
locate glest.ini
```

---

### Post by Taras on 2008-05-10
Oh tank you, all you had to do is hit alt + enter, but thanks everyone who tried to help i really aprriciate it 

thank you again

---

### Post by Perfect Storm on 2008-05-11
```
gedit ~/.glest/glest.ini
```

Change
Windowed=1
to
Windowed=0

RefreshFrequency=75
ScreenHeight=768
ScreenWidth=1024

can you set which fits your monitor.

In my case it would be

RefreshFrequency=60
ScreenHeight=1050
ScreenWidth=1680

---

### Post by daitheflu08 on 2008-06-26
This game looks great but I can't get it in fullscreen mode.  If I hit alt+enter it flashes to full screen and then back again.  I tried changing the windowed=0 and that has absolutely no effect at all.

Any ideas?

---

### Post by daitheflu08 on 2008-06-26
Here is how my glest.ini looks right now: 

; === Properties File === 

AiLog=0
AiRedir=0
CheckGlCaps=1
ColorBits=32
ConsoleMaxLines=10
ConsoleTimeout=1
DayTime=1000
DebugMode=0
DepthBits=16
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
ScreenHeight=600
ScreenWidth=800
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

---

### Post by atomkarinca on 2008-06-26
Are your desktop effects (Compiz, Beryl, what have you) on? If so then try running the game while they're off.

---

### Post by daitheflu08 on 2008-06-26
That fixed it for me, thanks.

---

### Post by atomkarinca on 2008-06-26
No problem.

---

