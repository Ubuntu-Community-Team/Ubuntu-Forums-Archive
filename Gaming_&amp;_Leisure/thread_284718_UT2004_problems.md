---
title: "UT2004 problems"
date: 2006-10-26
forum: Gaming &amp; Leisure
---

### Post by odbod on 2006-10-26
Ubuntu 6.06 kernel 2.6.15-27-386
Intel Pentium 4 w/ HT @ 3 ghz
1 gb ram
nVidia GeForce 7300 GS

NOTES: I have nvidia-glx latest from the ubuntu repositories and I have done the manual configuration of changing "nv" to "nvidia". Color depth at : 24  

----
I have UT2004 updated to 3369.2(linux of course). So, this is the problem. I can not change resolution! UT2004 just closes out when I switch to 1024 x 768. No matter what I do, I can delete UT2004.ini (it doesn't come back even when I start UT up again, yet all the settings are still there!!), replace it with Default.ini, change the resolution in the SLD area [and WinDrv(even though there was no point, I tried.)] and nothing happens, it stays at the same old 800 x 600.

Is there some way for me to change it? Here is a few things to know. I have tried using software rendering and changing the resolution. WORKS, but doesn't stay when I switch back to OpenGL, it just closes out. The LOG doesn't tell me anything fancy.

--
If I have no way of changing the resolution, is there some way to get above the 60 fps I keep getting?

---

### Post by aidanr on 2006-10-26
in your ~/.ut2004/system/ut2004.ini set the following

[Engine.Engine]
;RenderDevice=D3DDrv.D3DRenderDevice
;RenderDevice=D3D9Drv.D3D9RenderDevice
;RenderDevice=Engine.NullRenderDevice
RenderDevice=OpenGLDrv.OpenGLRenderDevice
;RenderDevice=PixoDrv.PixoRenderDevice

notice the ; to comment out the other renderers

[WinDrv.WindowsClient]
FullscreenViewportX=1024
FullscreenViewportY=768
StartupFullscreen=True

[OpenGLDrv.OpenGLRenderDevice]
UseVSync=False

if you still can't get above 60fps online, you can get around the framerate cap by making a couple of binds in your ~/.ut2004/system/user.ini

8=netspeed 20000
9=netspeed 10001

i press 8 and then 9 everytime i join a new map online and that uncaps my fps, you can change 8 and 9 to whatever suits

---

### Post by odbod on 2006-10-26
Cool, thanks. The ; things have already been done, I will do the vsync and do the uncap thing. 

And the resolution thing you posted, I already tried that. :S

---

### Post by odbod on 2006-10-26
I ran the game as root, and then tried resolution.. It closed, but I got this error:

Xlib:  extension "XiG-SUNDRY-NONSTANDARD" missing on display ":0.0".
X Error of failed request:  BadValue (integer parameter out of range for operation)
  Major opcode of failed request:  134 (XFree86-VidModeExtension)
  Minor opcode of failed request:  10 (XF86VidModeSwitchToMode)
  Value in failed request:  0x135
  Serial number of failed request:  290
  Current serial number in output stream:  291

Why is it that I can go to a resolution higher than 1024 x 768 and not have it crash like this.

---

### Post by gummygod on 2006-11-02
im having the exact same problem only with an ati radeon 9600.
and all the settings as aidanr posted are set like that since ut has been installed (for me at least).  no matter how much i change the ut2004.ini the resolution wont change.  also when i change defuser.ini or make a user.ini none of the binds work like they do for windows, i have to change with limited selection in the setting while running the game.  
so the big problem is not being able to change res away from 800*600.  anyone kno y changing ut2004.ini wont change resolution and y it crashes when u do it through the game? and better yet: how to fix it.

---

