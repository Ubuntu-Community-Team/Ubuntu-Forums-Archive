---
title: "GTA SA not running"
date: 2008-04-30
forum: Desktop Environments
---

### Post by snick512 on 2008-04-30
Aylo. I have GTA SA installed with both WINE and Crossover.

however , it will not run on wine because it says it can't find the CD/DVD.. so i set it in wine and it still complains (obviously i tried mounting it which it worked for the mount but wine still couldn't find it).

When i run it with Crossover it says "No ASPI layer found on your system. This is necessary for successful authentication."

I even tried using the noCD crack but still no luck.

btw I'm using

```

mount /home/ty/Public/gta-sa-v1.ISO /media/gta -o loop

```

For the mount command.

can anyone help me get this game running please?

---

### Post by jasonp on 2008-04-30
edit

---

### Post by shearn89 on 2008-04-30
The dvd should auto mount - you shouldn't need to mount it manually. Just double click on the desktop icon for it to make sure that its mounted, then try again. I'm not sure about the rest, but for gaming you may want to look a cedega - its like wine, but specifically designed for games, and they keep it pretty up to date. You have to subscribe, but thats only to get the latest updates, so i guess you could subscribe, download it, then unsubscribe?

---

### Post by snick512 on 2008-04-30
Nah, I have the ISO on my computer because  I use my DVD-ROM for other things, so i can't really tie that up. so mounting it and using the dvd-rom is basically the same thing.

and Cedega.. haven't thought about that.. but I'll try it. (I used to have cedega from a friend of mine but lost the CD one day lol)

I'll let know how it goes

---

### Post by snick512 on 2008-05-01
Nope. I tried Cedega and still no luck.

any other ideas?

---

### Post by aberry5555 on 2008-05-01
None to help really... but a quick question anyway, are you sure gta will work, I think only games that support OpenGL work, and I think gta sa is directx only.

---

### Post by soxs on 2008-05-01
Wine has its own dx implementation, so it may work.

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=7677](http://appdb.winehq.org/objectManager.php?sClass=version&iId=7677)
&
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=3780](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3780)

Compile the named wine version yourself for maximum chance to make it work, and for future wine related questions post in the section for wine.

---

### Post by aberry5555 on 2008-05-01
Oh, I didn't realise DX was supported now :)

---

