---
title: "America's Army wont start. No reasonable explalantion."
date: 2005-12-11
forum: Gaming &amp; Leisure
---

### Post by UltraSonicSite on 2005-12-11
I solved it, if you get the error 

> Can't find file for package 'PixoDrv'

History:

Exiting due to error 


then go to your home folder. Go to the menu View/View Hidden files. Find Arymyops and find the file ArmyOps.ini. Open it up and go to the line that says
```

[Engine.Engine]
;RenderDevice=D3DDrv.D3DRenderDevice
;RenderDevice=D3D9Drv.D3D9RenderDevice
;RenderDevice=Engine.NullRenderDevice
RenderDevice=PixoDrv.PixoRenderDevice
;RenderDevice=PixoDrv.PixoRenderDevice

```

or something similar. Just put a ; in all of them and take one off the second option, so it looks something like
```

[Engine.Engine]
;RenderDevice=D3DDrv.D3DRenderDevice
RenderDevice=D3D9Drv.D3D9RenderDevice
;RenderDevice=Engine.NullRenderDevice
;RenderDevice=PixoDrv.PixoRenderDevice
;RenderDevice=PixoDrv.PixoRenderDevice
```
Thats it!

> I installed **AA**

I logged in to **AA**

I played **AA**

I felt that It needed more FPS.

I lowered all the graphics to low.

I still felt it needed more.

I switched the OpenGL option to Software, out of curiousity, while a game was 
still running.

It crashed

Wouldn't start.

Reinstalled.

Wouldn't start.

And thats the whole story. The Same thing happened when I installed "Penguin Racer." It crashed and didnt work again until I reinstalled ubuntu. I little help here guys =P

---

### Post by M3ta7h3ad on 2005-12-11
You have tried the obvious of changing it back to openGL yeah?

---

### Post by UltraSonicSite on 2005-12-11
Well it wont start so eh, I can't do that. Unless theres a file I can change?

But like I said, I deleted it, and reinstalled and it still does not work.

---

### Post by UltraSonicSite on 2005-12-11
Here's what I get

```
ultrasonicsite@Ubuntu-Network:/usr/local/games/armyops$ armyops
Can't find file for package 'PixoDrv'

History:

Exiting due to error

```

---

### Post by M3ta7h3ad on 2005-12-11
My only guess is that it keeps its settings in a config file. Where that file is I have no idea. Have you tried searching the AA site?

---

### Post by UltraSonicSite on 2005-12-11
Ya I posted, they dont know what the prob is either. Also, another user in the AA forums also has this problem.

---

### Post by UltraSonicSite on 2005-12-11
Alright guys, I figured it out.

---

### Post by ATAQ on 2006-01-14
Hey what is the solution to this problem asd it has just happened to me?

---

### Post by Azion on 2006-01-14
Anyone try searching for the missing package?

---

### Post by buczi_poland on 2007-02-27
Hello, I'm buczi from Poland

Now you should be in something like a console version of Windows notepad. Fun stuff. Find the section that goes:


;RenderDevice=D3DDrv.D3DRenderDevice
;RenderDevice=D3D9Drv.D3D9RenderDevice
;RenderDevice=Engine.NullRenderDevice
;RenderDevice=OpenGLDrv.OpenGLRenderDevice
RenderDevice=PixoDrv.PixoRenderDevice


And try changing it to


;RenderDevice=D3DDrv.D3DRenderDevice
;RenderDevice=D3D9Drv.D3D9RenderDevice
;RenderDevice=Engine.NullRenderDevice
RenderDevice=OpenGLDrv.OpenGLRenderDevice
;RenderDevice=PixoDrv.PixoRenderDevice

hello, ;)

---

### Post by Zilulil on 2007-02-27
which version of AA are you guys talking about? Is it the last native linux one or 2.8 that is supposedly running under WINE but doesn't seem to like me.

---

### Post by Xkper on 2008-09-18
> **UltraSonicSite said:**
> Well it wont start so eh, I can't do that. Unless theres a file I can change?

But like I said, I deleted it, and reinstalled and it still does not work.

In the console:

```
armyops -opengl 
```

;)

---

