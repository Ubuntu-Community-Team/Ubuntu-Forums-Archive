---
title: "Helping getting portal to work"
date: 2007-11-11
forum: Gaming &amp; Leisure
---

### Post by JarvidLol on 2007-11-11
Ok. I'm using wine 0.9.49

Id the windows 98 thing. Im letting the window manager control the apps, and they run fine. 

I get the loading screen for portal and them it closes and I get an error message that says I don't have Directx 8.

I put the -dxbleh 80 thing in the launch options and everything.

My registry stuff in direct3D sez:

DXMode    80
DirectDrawRenderer opengl
PixelShaderMode enabled
UseGLSL disabled
VideoMemory size 128

Halp!:confused:

---

### Post by FG123 on 2007-11-11
What do you mean by the "Windows 98 thing"? Did you set WINE to emulate the Win 98 environment?

If so, how did you get Steam to work? Steam won't even RUN if it detects anything less than a Windows 2000 platform, ever since they added restrictions earlier in the year.

---

### Post by Polygon on 2007-11-11
steam will not work in windows 98 mode, try it in windows 2000

also, using reg edit, edit your registry keys to do this:

Under HKEY_CURRENT_USER\Software\Wine\Direct3D put in:

OffscreenRenderingMode fbo
PixelShaderMode enabled
UseGLSL enabled
VideoMemorySize (size in megabytes for your video card memory, I put in 256)


and also, i tried to get tf2 working, and i didnt get the menu screen in anything less then dxlevel 90....but your card must be super old if it doesnt support dx9 O.o

---

### Post by JarvidLol on 2007-11-11
> **Polygon said:**
> steam will not work in windows 98 mode, try it in windows 2000

also, using reg edit, edit your registry keys to do this:

Under HKEY_CURRENT_USER\Software\Wine\Direct3D put in:

OffscreenRenderingMode fbo
PixelShaderMode enabled
UseGLSL enabled
VideoMemorySize (size in megabytes for your video card memory, I put in 256)


and also, i tried to get tf2 working, and i didnt get the menu screen in anything less then dxlevel 90....but your card must be super old if it doesnt support dx9 O.o

Ok did that but I get the same error. saying portal needs a minimum of directx8 to start.

---

### Post by FG123 on 2007-11-11
I suppose the obvious question to ask is: do you know what kind of video card you have?

---

### Post by Polygon on 2007-11-11
and did you try forcing it using -dxlevel 90?

---

### Post by aoanla on 2007-11-12
> **FG123 said:**
> What do you mean by the "Windows 98 thing"? Did you set WINE to emulate the Win 98 environment?

If so, how did you get Steam to work? Steam won't even RUN if it detects anything less than a Windows 2000 platform, ever since they added restrictions earlier in the year.

What you do, is that you set hl2.exe to Windows98 mode, and steam.exe to WindowsXP (or whatever), and then Wine only runs the HL2/Source engine binary in Windows98 mode, so Steam doesn't complain.

This has helped stability for quite a few people...

---

### Post by JarvidLol on 2007-11-12
Ok i have done what oanla and penguin guy said but i still get the same error. 

This game requires a minimum of directx 8 to play.

My vieo card supports DirectX 9.

---

### Post by Sockerdrickan on 2007-11-12
And you tried different dxlevel? and winedebug=-all ?

---

### Post by JarvidLol on 2007-11-12
Yes except I don't get how winedbug works. I typed it in the terminal and nothing happened.

---

### Post by JarvidLol on 2007-11-12
Still won't work in windowed mode.

---

