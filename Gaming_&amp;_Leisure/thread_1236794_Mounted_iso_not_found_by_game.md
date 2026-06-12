---
title: "Mounted iso not found by game"
date: 2009-08-10
forum: Gaming &amp; Leisure
---

### Post by Raff1 on 2009-08-10
Hello! I noticed that Wine-related questions gets deleted.. My problem is involving Wine, but Wine itself is not the issue here, so I hope the question is related to this forum.

I have installed a copy of Diablo II + Expansion and made a .iso of my CD. I am able to run the game (using wine) with the original CD in the cd-rom but when I mount the .iso the game is not able to find it.. I get the message "Please insert expansion disk". I have tried to mount the .iso to /media/CD (which I made my self with mkdir) and /media/cdrom without results. I am able to browse the virtual CD however. When I browse the virtual CD I am able to run the setup.exe on the CD when mounted on /media/cdrom but not when mounted on /media/CD (in the latter case I get prompted with "insert cd").

I mounted like this:
```
sudo mount -o loop /path_to_iso/D2.iso /media/cdrom
```So why dont the game recognize the mounted image?

Should I have monted the image in a special way or place?
Is some crucial part of the .iso not included while mounted like this?
Is there some application I can use (like daemon tools for windows) to get it to work properly?

I really hope you can help me out here! =)

Regards, Raff1

---

### Post by 569874123 on 2009-08-10
[QUOTE=Raff1;7765012]
Is there some application I can use (like daemon tools for windows) to get it to work properly?/QUOTE]

[http://www.acetoneteam.org/](http://www.acetoneteam.org/)

---

### Post by Raff1 on 2009-08-12
> **569874123 said:**
> [quote=Raff1;7765012]
Is there some application I can use (like daemon tools for windows) to get it to work properly?

[http://www.acetoneteam.org/](http://www.acetoneteam.org/)[/quote]

Thanks! It made no difference however.. The game didn't recognize the image (it gets recognized with daemon tools on windows, so the image itself is ok).

Do I have to mount in a special way or place the game will look for it in (like the cd-rom)? As previously noticed mounting it directly to /media/cdrom didn't work..

---

### Post by JayKay3000 on 2009-08-12
This is just a wild guess but have you or can you set wine to recognize the virtual drive under the drives option in wine?

I can only imagine wine is simply not finding the path to the drive and going to the empty drive and going 'no disk here' and not considering the image.

However bf2 I had the same prob in windows because the game would not read image files.

---

### Post by Raff1 on 2009-08-12
[quote=JayKay3000]This is just a wild guess but have you or can you set wine to recognize the virtual drive under the drives option in wine?

I can only imagine wine is simply not finding the path to the drive and going to the empty drive and going 'no disk here' and not considering the image.[/quote]

I added /media/CD as F: to the wine drivers and then it finally worked! Thanks. Looks like it was a wine related issue after all...

[quote=JayKay3000]However bf2 I had the same prob in windows because the game would not read image files.[/quote]

This worked fine with me in this case =)

Thanks again!
Regards, Raff1

---

