---
title: "Age of Mythology"
date: 2006-03-24
forum: Gaming &amp; Leisure
---

### Post by sebz2005 on 2006-03-24
Uh, has anyone been able to run Age of Mythology on Ubuntu?

---

### Post by rockrhino27 on 2006-03-24
I tried a while back using Cedega.  I actually bought a Linux Program.  That was a first and a waste of 15 dollars.  Cedega uses WINE, and I got just as far with both programs.  I was able to Install AoM, but after the installation I could not play the game.  It is my understanding that WINE and Cedega will act the same way for all "Age" games published by Microsoft.  ](*,)

---

### Post by sebz2005 on 2006-03-24
Aw well. Thanks anyway.

---

### Post by YokoZar on 2006-03-24
[QUOTE=rockrhino27]I tried a while back using Cedega.  I actually bought a Linux Program.  That was a first and a waste of 15 dollars.  Cedega uses WINE, and I got just as far with both programs.  I was able to Install AoM, but after the installation I could not play the game.  It is my understanding that WINE and Cedega will act the same way for all "Age" games published by Microsoft.  ](*,)[/QUOTE]
Cedega uses a version of Wine that is aproximately 2 and a half years old.

Looking at the Applications database, it appears Age of Mythology could be coaxed into working in Wine with version 0.9.3 a couple months ago:

[http://appdb.winehq.org/appview.php?versionId=3765&iTestingId=589](http://appdb.winehq.org/appview.php?versionId=3765&iTestingId=589)

You will likely need a No-CD crack to get the game to work (Copy protection is notoriously difficult in Wine), however I'd wager with that the game will work with the latest version of Wine.  Give it a try and see what happens.

---

### Post by Harleen on 2006-03-25
Age of Mythology is one of the very few games, that actually worked for me using plain wine. I just did what the link given by YokoZar said: Install, add no-cd patch, reduce graphic quality. That's it.
Interestingly I never got Age of Empires II to work...

---

### Post by roostishaw on 2006-05-02
Hello, sorry to 'revive' an old thread, but...
Harleen, how were you able to eject the second disk during installation? Also, how do you apply the no-cd patch?

Thanks!

---

### Post by Harleen on 2006-05-03
I just did the entire installing procedure to verify how I did it. 
At first mount the CD to /mnt/cdrom (it usually does that automatically).
Then start the installation process from anywhere but that directory! If you have a shell open on that directory, you won't be able to eject the disc later. This will work:
```
cd ~
wine /media/cdrom/SETUP.EXE
```

When the installation is asking for the 2nd CD you can unmount the CD by hand  by typing 
```
umount /dev/cdrom
```
Then change the CD and mount the other CD with 
```
mount /dev/cdrom
```

Et voila - that's it.
You probably can do that mounting by clicking on fancy icons on your desktop, but since I don't know whether you are using GNOME or KDE and I'm always using the command line I'll stick with the way, that's known to work.

If you try to run the game now, it will ask you to unload the debugger. That's what we need the No-cd patch for. You may also call it a crack, if you like. And for obvious reasons I cannot tell you where to get it and how to use. But google can...

But after installing the game I had to realise, that the game now doesn't work for me anymore.  Since the last time it ran I changed the computer, switched to Dapper and use a later wine - and something did break it. :-s

---

### Post by roostishaw on 2006-05-07
Harleen, check your pm's.

---

### Post by thunderduck3141 on 2006-07-17
yes aom only works in wine 0.9.13 
it really frustrates me, but i dont know how to get to versions working on one system
anyone get bw2 working, its been a project for me, im so close, go to the google wine group or look at bith posts i made in gaming central that no one answered, at all

---

