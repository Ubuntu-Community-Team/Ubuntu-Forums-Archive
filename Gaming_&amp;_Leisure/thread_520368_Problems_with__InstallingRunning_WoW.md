---
title: "Problems with  Installing/Running WoW"
date: 2007-08-08
forum: Gaming &amp; Leisure
---

### Post by platypuz on 2007-08-08
So I was attempting to install WoW using this guide:

[http://ubuntuforums.org/showthread.php?t=31248]("http://ubuntuforums.org/showthread.php?t=312482")

After getting through the initial install with wine, I continued on to the next steps and that is where I found my problem, at stage eight I ran the following command in the terminal:

```
gedit ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft/wtf/Config.wtf
```

and in the window that results from that command, just as the guide told me to, I placed:

```
SET SoundOutputSystem "1"
SET SoundBufferSize "150"
SET gxApi "OpenGL"
```

However, when I tried to save the file with the sound settings in it I got a error message saying that the directory I was attempting to save to could not be found. 

I am attempting to run WoW:BC if that makes any difference as to the use of the guide I was using. 

Also, after getting  that error message a few times, I attempted to simply play the game and hope that it would work. The game loaded but  I got a terrible frame rate (even before I logged in). 

I have a Nvidia Geforce FX 5500 graphics card. I suspect this could be the problem with the frame rate as I have read in other threads that wine makes you take a hit in the fps department. 

Any help would be greatly appreciated 

Platypuz

---

### Post by misconfiguration on 2007-08-09
What is your driver version?

I had a similar issue with Wine + WoW until I had manually updated to the latest Linux Nvidia drivers.

---

### Post by Nkari on 2007-08-09
Maybe try navigating to the file through the graphical fie browser at the desktop level and then editing.

Just sounds like you didn't find the file properly you were trying to edit or something.

I don't think you are having videocard driver issues yet.

You will need to type in the part of the path to the wine directory as the bit with the dot is hidden to that browser.

Maybe someone can explain that better than me. I've been stuck using windows for a couple of weeks.

---

### Post by Kushkah on 2007-08-09
The WTF directory part is case-sensitive, should be all-caps. Or at least that's how mine is, I tried both ways on my system and only this way worked.

```
gedit ~/.wine/drive_c/Program\ Files/World\ of\ Warcraft/**WTF**/Config.wtf
```

---

