---
title: "Need help with games and wine"
date: 2006-08-07
forum: Gaming &amp; Leisure
---

### Post by langer.afc on 2006-08-07
Hello everyone. This is my first post here :D 

I am somewhat new to linux, so I'm kind of lost here. I've been trying to run  a couple of games in wine, but with no luck. I was almost able to run WarCraft III - Frozen Throne, but I couldn't use it because of CD problems (I have original CD, but it wouldn't see it, even if it was in the drive).

When I tried running Rome - Total War, it says that it can't find DirectX (which I'd expect, but have no idea how to deal with).

Can anyone help me?
Thanks a lot,
Paulo

---

### Post by darrenm on 2006-08-07
You will get lots of help and information here: [http://www.linux-gamers.net/](http://www.linux-gamers.net/)

With WOW I believe you actually need a no-cd crack as the copy protection doesnt correctly see the CD through the wine layer.

I think with standard wine you need games to be able to run in opengl mode rather than directx. If you have to have directx support try WineX/Cedega [www.transgaming.com](www.transgaming.com)

---

### Post by langer.afc on 2006-08-07
Well, I don't HAVE to have DX, I suppose. Can you help me get some OpenGL support then?

Thanks

---

### Post by darrenm on 2006-08-07
Im sorry, I havent used that game so I don't know if it even supports opengl.

---

### Post by AirRaven on 2006-08-07
> **langer.afc said:**
> I was almost able to run WarCraft III - Frozen Throne, but I couldn't use it because of CD problems (I have original CD, but it wouldn't see it, even if it was in the drive).

I had the same problem- it's easily fixed. Just run [FONT="Courier New"]winecfg[/FONT] from the terminal, and click the "Drives" tab. Click "Autodetect". Then try. If that fails, just reinstall Warcraft III from the CD.

If it runs slowly, run WC3 with the -opengl switch after it in the command line ([FONT="Courier New"]wine war3.exe -opengl[/FONT]). If you have no sound, or sound problems, just click the "Audio" tab in [FONT="Courier New"]winecfg[/FONT] to let Wine autoconfigure the sound.

Bear in mind that Wine doesn't play the FMV in Warcraft 3- but you can view those by simply loading the video files with MPlayer or any other decent media player.

---

