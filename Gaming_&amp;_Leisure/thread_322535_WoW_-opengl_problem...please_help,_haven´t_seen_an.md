---
title: "WoW -opengl problem...please help, haven´t seen anyone with this issue before!"
date: 2006-12-20
forum: Gaming &amp; Leisure
---

### Post by murraysw on 2006-12-20
Alright here´s the deal - 

I´m running Ubuntu 6.10 Edgy AMD64 version with Beryl...Nvidia drivers...(they work)

I have WoW installed, it runs in -d3d9, but looks like ****.  When I try to run it in -opengl, as soon as I click my character to ¨Enter World¨ (load the game) ...it freezes about 2 seconds into loading (1/6th of the way)...and the console spits out:

err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0
err:wgl:ConvertPixelFormatWGLtoGLX invalid iPixelFormat 0

I don´t know what to do.  I´ve already turned off/down all of the video options (just loaded the game in d3d and turned it all off) ...and the problem still happens

Anyone got any ideas?

---

### Post by murraysw on 2006-12-20
Solved it.

It turns out that you CANNOT load WoW in opengl mode using an emulated desktop area with wine!  You *must* turn off the ¨Emulate Desktop¨ option and use WoW´s native window-mode options in its video options...

So for anyone else experiencing WoW freezing while loading using Opengl, this is the fix!

Someone should likely document this somewhere.

---

### Post by hikaricore on 2006-12-20
I'm able to run wow in an emulated desktop window using opengl without using it's "windowed" mode.

Must be specific to your video card.

---

### Post by murraysw on 2006-12-21
What card you using?  I´ve got a Nvidia 7600GT in here with the latest beta Nvidia drivers.

---

### Post by Naegling23 on 2006-12-21
wow, im jeleous, Im unable to run wine on beryl, it refuses to go fullscreen.  

Im wondering how you got everything running?

---

### Post by hikaricore on 2006-12-21
> **murraysw said:**
> What card you using?  I´ve got a Nvidia 7600GT in here with the latest beta Nvidia drivers.

I could do this with my integrated intel (junk) chipset for over a year now, and I can still do it on my nvidia gforce 6200.  lol  I think you may just have bad luck.

---

### Post by chadk on 2006-12-21
Yeah I removed Beryl so I could run WoW without crashing either before or after running WoW in it's own X server.

---

### Post by hikaricore on 2006-12-21
Might I ask why you didn't just disable beryl from beryl-manager when you wanted to play direct rendered games instead of removing it?  O.o

Or maybe I'm misunderstanding you lol.  Just curious.

---

### Post by reiki on 2006-12-21
I have a 7300GT and I can run WoW in Wine (openGL) with Beryl running. However with Beryl running it cuts my framerate in WoW in half. So I turned Beryl off.

nVidia 9629 drivers if I remember correrctly. On Edgy

---

### Post by chadk on 2006-12-21
Didn't know you could ;) Thanks hikaricore!

---

### Post by chadk on 2006-12-22
ok, I give up, how do you turn it off?
I've selected QUIT from the Beryl Manager but that doesn't actually stop any of the animations or anything it just closes the beryl-manager... ?

---

### Post by Naegling23 on 2006-12-22
click on the red gem icon, and go to composite manager (I think, im not actually at my home computer).  You can change between beryl, and whatever else you have.  For me, its kwin (kde).  For ubuntu, im imagining its metacity.  This will dissable all the beryl effects, but still leave the manager running.  When your finished playing, you just switch it back.

I would be interested in hearing how others get wow on full screen in beryl.  Im not worried about frame rate drops, I run doom3 on beryl without a problem.  When I try to run wow with beryl enabled, the screen does some funky things, wow "hangs" off the edge, and I have to ctl+alt+bcksp out of there.

---

### Post by chadk on 2006-12-23
Ah.. I don't have "Composite Manager" or anything like it.
I see, it's "Select Window Manager" on my version.  Cool, thanks! :)

---

