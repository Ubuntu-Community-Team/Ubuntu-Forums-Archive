---
title: "Warcraft: The Frozen Throne"
date: 2007-05-20
forum: Gaming &amp; Leisure
---

### Post by dachinster on 2007-05-20
After unsuccessfully trying to get my store bought Warcraft III Reign of Chaos and The Frozen Throne to work in Wine, i paid for 3 months of Cedega just to get the software to try it.

Reign of Chaos installed just fine and i can play it pretty well.

The Frozen Throne hangs on install (yes i am installing it to the same folder as ROC).

It starts to install just fine and then gets stuck near the end.
I have tried this twice.
The first time, i left it for an hour and then cancelled.
Currently i have it still in this state (2 hours now) and my cdrom drive has stopped spinning and i am not seeing any activity at this time.

I have attached a screenshot to show you where it is stuck

---

### Post by dachinster on 2007-05-21
anyone?
it is now several hours later and i even went to sleep and the thing is still hung on install and the pc is hardly moving at all to type this msg...

we can safely say the game crashed again on install

---

### Post by blackjackel on 2007-05-21
You could try installing the game through windows, then running it off ubuntu... like I did.

---

### Post by dachinster on 2007-05-21
ok, i finally got frozen throne to install

i made an alcohol image in windows, booted into ubuntu, used mdf2iso and created an iso file, mounted that to my /media/image and it installed!

now my only problem is that cedega asks for the cdrom when i run the game.... just like wine...

is there anyway i can get the game to mount such that cedega sees the mount folder as a cdrom?

i have tried mounting the image to /media/cdrom0 but i get the same results... cedega asks for the cd

---

### Post by blackjackel on 2007-05-21
in wine the command is winecfg, so maybe for cedega its cedegacfg? in any case you have to get to the config for cedega and set the mounted image as a cd rom drive under there. It SHOULD work then.

Good luck.

---

### Post by dachinster on 2007-05-21
thanks for your help throughout most of my threads blackjackel :)

but no, there is no cedegacfg

this definitely is some problem whereby ubuntu is not seeing the mount drive as a cdrom even though i have set it to /media/cdrom and /media/cdrom0 (symbolic link)

in both those cases, cedega asks for the cd, and when i put the original cd in, it works... but i do not want to risk scratching the disk, hence why i made the image

is it possible that when i used mdf2iso, it did not copy whatever copy protection the alcohol image had?
the alcohol image i made copied the disc 1:1 perfectly, including the copy protection...
is it possible that mdf2iso left it out?

---

### Post by dachinster on 2007-05-21
ok i figured it out.
i booted into windows and tried to mount the warcraft.iso and it failed asking me for the cd.
apparently only the mdf file works and ubuntu fails to mount the copy protected warcraft.mdf file

apparently warcraft is protected by securom 4.8xxxx and an iso file cannot support this type of copy protection.
therefore only the mdf file type could properly emulate the protection.

since i am using an original cd and not a cracked game, i need to get a no-cd crack (which sucks becuz i wont be able to update warcraft without putting in the original cd and reverting back to the original exe)

on the whole, this experience has taught me that linux has a long way to go and its back to windows for gaming for me

---

### Post by Cappy on 2007-05-21
*cough* Blizzard doesn't care **** *cough*

---

### Post by dachinster on 2007-05-21
yes i know that...
no one cares about linux
<0.02% ~ nobody
hopefully linux will improve for next time and will include support for non-udf / non iso9660 file formats because apparently the copy protected mdf file is neither of them

---

### Post by Cappy on 2007-05-21
> **dachinster said:**
> yes i know that...
no one cares about linux
<0.02% ~ nobody
hopefully linux will improve for next time and will include support for non-udf / non iso9660 file formats because apparently the copy protected mdf file is neither of them

actually linux is more like .8% of internet users

---

### Post by dachinster on 2007-05-21
i was talking about those that are gamers in linux and out of that, those that play warcraft

---

