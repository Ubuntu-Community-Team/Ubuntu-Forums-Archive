---
title: "nexiuz choppy"
date: 2005-12-15
forum: Gaming &amp; Leisure
---

### Post by nalmeth on 2005-12-15
I just installed nexiux, and it looks really sweet, but I am getting very bad frames per second. For one thing, I don't know how much RAM my graphics card is using. I can't seem to figure out how to do that yet.
Barring that, I am hoping there is a way to just tweak this game, although changing resolution didn't make very big difference. 
Every sound in the game echos while the video studders, and it is unbearable. Could the sound in some way be at fault?

*Better yet, does anyone know how to adjust video card ram settings?*

thanks for any idea/refferal

these other post of mine are relevant:
[http://ubuntuforums.org/showthread.php?p=575852#post575852](http://ubuntuforums.org/showthread.php?p=575852#post575852)
[http://ubuntuforums.org/showthread.php?t=103876](http://ubuntuforums.org/showthread.php?t=103876)

over and out :cool:

---

### Post by hav0x on 2005-12-16
dont use sdl use the glx client. And it is still a game that is being developed ... to me it seems poorly optimized, so never expect great performances.

---

### Post by linbetwin on 2005-12-16
I tried nexuiz both in Ubuntu and Windows XP and I had the same choppy images and echoed sounds. After a while I gave it up and just deleted the game. I didn't know about the sdl/glx thing.

---

### Post by Fibre on 2005-12-16
I only tried it with xp and it said the recommended requirements where below what I had at the time, so I tried it. And what you've said here, sounds just like what happen when I tried it. 
I was hoping things might have changed with this game using ubuntu perhaps not.

---

### Post by hav0x on 2005-12-16
I have it installed and running pretty well with a fluid framerate(~40 :| ) good sound and all. But i had to give up the detail for performance (lower resolution (800x600) turn off details like bloom decals and mapping, so it looks like crap). It's a new engine, it needs a lot more work, imho it's not ready for mainstream gaming, has a LOT of issues.
Like i said the sound issue is with the sdl executable/sdl itself, i get it too, while running the glx one it just works. I say dl it and install it for the sake of experimentation, it really doesnt have the fun factor yet.

---

### Post by handy on 2005-12-16
If graphics are driven by an onboard chip, then you may be able to adjust the amount of shared system RAM that gets allocated to graphics only.  To do this you will need to go into the BIOS directly after boot-up.  This is usually done by holding down the "delete" key in the first stage of booting.  You will then need to find the setting & adjust it if you can. 

If you have the manual for your motherboard, you will find instructions towards the back of the book re: the BIOS settings.

I hope that helps,

handy

---

### Post by nalmeth on 2005-12-17
right on
i lost track of this post
thanks for info all.. nexiuz might be new, have lots of issues, run like crap, etc..
but it is an open-source game, and undoubtedly will improve.
its not like we paid for it or anything. I think it looks cool, and I hope to see improvements soon..

thanks especially handy, I will check my ram settings right now

BTW, what is GLX?
I had to install sdl when trying to compile some game from source, so thats all I have and all I know about.
Is GLX simple to obtain? SDL sure wasn't.

thanks again dudes

---

### Post by jaakan on 2006-02-25
On board video/gfx chip sets are not normally made for games. only seems true for one in Laptops. Their ram is shared with system ram. yes you can set shared ram, 32mb, 64mb, 128mb... just for the video/gfx chip but it's not the same as real Video ram. Data tranfer rates are very slow.

nexiuz is currently up to version 1.5, just came out and the engine has been improved big time.

I have a VIA/S3 Unichrome PRO IGP built-in video/gfx chipset until I get a addon video card my Ubuntu AMD 64bit pc is a Nexiuz game server which is fine with me. I use my 2 other pcs as clients. P3-666, 512Mb, NV GF2 GTS and P4/m 1.6Ghz, 512Mb, Intel 915. if you do have try the drivers for the VIA/S3 Unichrome PRO IGP someone posted a link for on this site if it's to slow too be playable buy a addon card. 



[QUOTE=nalmeth]right on
i lost track of this post
thanks for info all.. nexiuz might be new, have lots of issues, run like crap, etc..
but it is an open-source game, and undoubtedly will improve.
its not like we paid for it or anything. I think it looks cool, and I hope to see improvements soon..

thanks especially handy, I will check my ram settings right now

BTW, what is GLX?
I had to install sdl when trying to compile some game from source, so thats all I have and all I know about.
Is GLX simple to obtain? SDL sure wasn't.

thanks again dudes[/QUOTE]

---

### Post by charlieg on 2006-02-27
If you have issues, first thing you need to try is disabling some of the various effects. Several of the effects require things like shaders which can really impact performance if not directly supported by your graphics card.

---

### Post by e^e on 2006-02-28
nexuiz 1.5 has smoother netcode, make sure you choose a 1.5 server.

---

### Post by Asraniel on 2006-02-28
please report your problems in the nexuiz forum, like that the developers know it and can try to fix it in the next version!

---

