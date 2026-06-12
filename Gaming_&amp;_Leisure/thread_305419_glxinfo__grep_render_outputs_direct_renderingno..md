---
title: "glxinfo | grep render outputs direct rendering:no."
date: 2006-11-23
forum: Gaming &amp; Leisure
---

### Post by D_jmc on 2006-11-23
Hello all,

Running this command in the terminal
```
glxinfo | grep render
```

shows me this output
```
direct rendering: No
OpenGL renderer string: GeForce 7800 GT/PCI/SSE2/3DNOW!

```

I Can run beryl fine gives me all the effects with no problems and no slowdowns what so ever.

But the ```
direct rendering: No
``` worries me, I'm going to try half life 2 through cedega, as running steaminstall.exe with wine tells me to turn off the compatability mode.

Also I understand that I will have load Metacity (gnome windows manager) before launch cedega, am I correct in thinking this?

Cheers.

---

### Post by hikaricore on 2006-11-23
If direct rendering results in No, that usually means your processor is doing all the work for the video card.  Beryl may work just fine but I doubt your video card is doing any of the rendering.  Have you tried installing the latest drivrs for your video card?

---

### Post by D_jmc on 2006-11-23
I formated and installed Dapper (was using Edgy) and installed the latest drivers - x86 1.0-9626. and it has sorted out the problem

the out put of ```
glxinfo | grep render
``` is now ```
direct rendering: Yes
OpenGL renderer string: unknown board/PCI/SSE2/3DNOW!
    GL_NVX_conditional_render, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod,
```

The strange thing is, is that I had these drivers installed in Edgy....

Thanks for the input.

---

### Post by hikaricore on 2006-11-24
> **D_jmc said:**
> I formated and installed Dapper (was using Edgy) and installed the latest drivers - x86 1.0-9626. and it has sorted out the problem

the out put of ```
glxinfo | grep render
``` is now ```
direct rendering: Yes
OpenGL renderer string: unknown board/PCI/SSE2/3DNOW!
    GL_NVX_conditional_render, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod,
```

The strange thing is, is that I had these drivers installed in Edgy....

Thanks for the input.

Glad you were able to solve your problem :)

I had a similar issue upon upgrading to edgy, luckily someone on the boards  had released a working copy of i810 driver for my chipset. :)

---

### Post by Zelos on 2007-11-12
Is there any way we can check what our 3d grapihcs card is?
And what it this 'terminal' thing we have to enter that code into... basicly what is a terminal.

My Computer is a window xp with about 750 ram (enough to run world of warcraft) but do you think you know what  grapic card i may have that as i need to run world of warcraft on my computer. 

Can you please reply as soon as possible as i need to find out preety soon to see wether i can run world of warcraf or not on my coputer. 

Everything else i have under controll !!!!!!!!!

Thnx...........

---

### Post by cogadh on 2007-11-12
> **Zelos said:**
> Is there any way we can check what our 3d grapihcs card is?
And what it this 'terminal' thing we have to enter that code into... basicly what is a terminal.

My Computer is a window xp with about 750 ram (enough to run world of warcraft) but do you think you know what  grapic card i may have that as i need to run world of warcraft on my computer. 

Can you please reply as soon as possible as i need to find out preety soon to see wether i can run world of warcraf or not on my coputer. 

Everything else i have under controll !!!!!!!!!

Thnx...........
Um, this forum is for gaming on Ubuntu Linux, not Windows. Nothing you will read here will help you with a Windows XP computer.

---

### Post by hikaricore on 2007-11-12
Closed..

---

