---
title: "WoW under wine - low framerate"
date: 2006-02-18
forum: Gaming &amp; Leisure
---

### Post by DrKoi on 2006-02-18
Hi,

I've got WoW working under wine with the help of an excellent howto on this forum, but I'm not happy with the framerate I get (8-12 fps in areas with no other players around).

my system:

* hardware
- cpu: AMD Athlon(tm) 64 Processor 3200+
- video: ATI RADEON RX800
- sound: Creative Labs SB Live! 5.1

* software
- Ubuntu 5.10
- ATI drivers 8.22.05
- Wine 0.9.8 (patched with a wow fix)
- WoW 1.9.4

* settings
- both desktop & WoW are set to 1280x1024 at 85Hz
- I start WoW with *nice -n 19 wine "/home/koi/.wine/drive_c/Program Files/World of Warcraft/WoW.exe" -opengl*

(the "nice -n 19" was necessary to fix choppy sound)

And when I do **glxgears -printfps** I get:

39758 frames in 5.0 seconds = 7951.533 FPS
56630 frames in 5.0 seconds = 11246.209 FPS
51252 frames in 5.0 seconds = 10250.289 FPS
59845 frames in 5.0 seconds = 11968.964 FPS
66072 frames in 5.0 seconds = 13214.354 FPS

I read somewhere that enabling sound can dramatically decrease your framerate in wine, but I'd like to keep my sound...

Any tips on how I can increase performance?

---

### Post by DrKoi on 2006-02-22
I found a solution!

I installed Windows 2000 and now I get 85-95 fps :) 

So long Ubuntu, it just isn't worth all the trouble you need to go through to play games:

- finding & installing ATI drivers
- patching, compiling & installing wine
- browsing forums & playing with sound settings to fix that choppy sound

Installing Ubuntu & getting to a still unplayable WoW took a little more than a week.

Installing Windows 2000 with all necessary drivers, firewall, virusscanner & world of warcraft + patches took about 4 hours (including 1 hour for formatting the hard drive), and my framerate increased tenfold...

---

### Post by jason.b.c on 2006-02-22
I found a solution!

> I installed Windows 2000 and now I get 85-95 fps

So long Ubuntu, it just isn't worth all the trouble you need to go through to play games:

- finding & installing ATI drivers
- patching, compiling & installing wine
- browsing forums & playing with sound settings to fix that choppy sound

Installing Ubuntu & getting to a still unplayable WoW took a little more than a week.

Installing Windows 2000 with all necessary drivers, firewall, virusscanner & world of warcraft + patches took about 4 hours (including 1 hour for formatting the hard drive), and my framerate increased tenfold...


:( well that kinda sucks , sorry to here ya give up on ubuntu so soon!??:o 
but the thing you could try is a duel boot, then at least you've got the best of both worlds...;)

---

### Post by DrKoi on 2006-02-22
> but the thing you could try is a duel boot, then at least you've got the best of both worlds...

Yeah I tried that, and Grub messed up my MBR, leaving me unable to boot both Ubuntu or Windows (I got this "Error 17", and I couldn't fix it with a live session - grub refused to recognise my harddrive)

Only I had was to format my harddrive, and that kind of the "final drop" that pushed me back to windows. I'm not happy with it, but WoW is the main reason I turn my computer on...

---

