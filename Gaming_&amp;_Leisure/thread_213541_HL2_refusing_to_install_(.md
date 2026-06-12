---
title: "HL2 refusing to install? :("
date: 2006-07-11
forum: Gaming &amp; Leisure
---

### Post by sponge008 on 2006-07-11
[http://ubuntuforums.org/showthread.php?p=1237154#post1237154](http://ubuntuforums.org/showthread.php?p=1237154#post1237154)

Since this, I have also tried using this script:
```

#!/bin/sh
cd /home/yuri/.wine/drive_c
cd "Program Files"
cd Steam
WINEDEBUG="-all" wine Steam

```

to run Steam, and it didn't help any more than just browsing to the directory and sudo wine steam.exe. However, using nothing more than quick reflexes and multiple tries, I got a screenshot of the window that pops up for a nanosecond when I launch Steam. It is "Updating Steam" with only a cancel button. It then disappears. Wine Desktop then stops responding. So, does anyone know what I can do to fix this? I'm running the latest version of Wine. ](*,)

---

### Post by vem0m on 2006-07-11
well aside from this shoudl have remained with the old other topic all i can possibly see is why in the world would u load wine with the sudo command?

---

### Post by sponge008 on 2006-07-11
> **vem0m said:**
> well aside from this shoudl have remained with the old other topic all i can possibly see is why in the world would u load wine with the sudo command?

It doesn't work well without root access. Note that it's 
sudo wine steam.exe, and not
sudo steam.exe

---

### Post by vem0m on 2006-07-11
yes well still u shouldn't ever have to use sudo with wine

---

### Post by sponge008 on 2006-07-11
!!!
The Steam installation didn't work if I didn't sudo it, if I remember correctly. Something seems very wrong.

---

### Post by vem0m on 2006-07-11
yes it seems wierd unfortunatly i am out of ideas as i have yet to try and install steam again :(

---

### Post by sponge008 on 2006-07-11
Could the problem be with my installation of Ubuntu/Ubuntu itself?

---

### Post by vem0m on 2006-07-11
unlikly more possible with the copy of wine u are running check ur wine config by going to terminal and typing winecfg and sudo winecfg to change roots config beyond that i do not know if what u check doesn't work i'd wait for another person to try and assist u as that is all i can come up with my apologies

---

### Post by Jasper Houtman on 2006-07-11
You probably forgot to install Mozilla active X control b4 installing steam, click on this [link]("http://appdb.winehq.org/appview.php?iVersionId=1554") and scroll down for a howto on installing steam.

---

### Post by vem0m on 2006-07-11
i got it going to Cedega so far wine failed me with a systray crap but cedega has it going :D

---

### Post by sponge008 on 2006-07-11
I have the Mozilla activex control installed. I guess if nothing else comes up, I'll try Cedega.

---

### Post by sponge008 on 2006-07-11
I tried Cedega. Steam finally worked! However, with both CSS and HL2 updated, when I launch CSS, a black screen pops up for a few seconds, just like on Windows, then the "loading..." screen comes up, then again a black screen. What is going on!?!?!

Also: the fonts in Steam were messed up, so I copied every .ttf from my Windows Fonts folder to the drive_c of cedega in windows/fonts. However, this did not help. How is this problem fixable?

---

### Post by vem0m on 2006-07-11
which version of cedega are u using? E.G version number Paid or CVS?

---

### Post by sponge008 on 2006-07-12
I'm using full version 5.2.2. I may mention, after I get the black screen, I can move my mouse around on a 800x600 black area where CSS would be. However, there is no sound/visual. Also, when I try to wine the steam that Cedega installed, it freezes while logging on.

---

### Post by vem0m on 2006-07-12
hmmmmm well its the same data either thu wine or cedega only thing i can think of is its not loading right u did however select the game profile Steam in the GDDB right?

---

