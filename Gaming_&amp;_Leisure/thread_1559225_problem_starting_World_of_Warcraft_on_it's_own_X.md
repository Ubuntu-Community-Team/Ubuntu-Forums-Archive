---
title: "problem starting World of Warcraft on it's own X"
date: 2010-08-23
forum: Gaming &amp; Leisure
---

### Post by Zirts on 2010-08-23
Hi,

I recently read this page here: [WorldofWarcraft/Troubleshooting]("https://help.ubuntu.com/community/WorldofWarcraft/Troubleshooting")

And found this article:
> 
**ATI / AIGLX**
Please be aware that People using AIGLX may experience low framerates.

As a test, one can do this:
```
 /etc/init.d/gdm stop          # this will shutdown your X Server!
 startx `which wine` WoW.exe   # start X with WoW as "Desktop Manager" (might look funny :])
```

Running AIGLX and another X Server running wow will probably crash the box, so please dont try that or make sure you can ssh to the box.

My personal experience is ~5-10 FPS with wow inside aiglx, while 25-30 fps running on a "standalone X Server"


Now what I did: 
I made a executeable text file to /home/kaspar/Töölaud/
File name: lol
Contents: ```
startx `which wine` Wow.exe
```

Now I made a copy of the Wow.exe to wines system32 folder, otherwise the script didn't work.

Ok, now I start killing the X, Ctr + Alt + T, and I type in 
```
sudo /etc/init.d/gdm stop
``` 
It asks for my password, I give it to him, then it informs me that I can use that script in other way too but non-the-less, it kills the X, now I see a black screen with a lot of text on it as I'm using the "KMS with a Radeon card" function.

Ok seems cool, I managed to get here, now I press the combo: Ctrl + Alt + F2 and on that screen I log in with kaspar, enter my password and I'm ready to start Wow.exe with X.

```

cd /home/kaspar/Töölaud/

./lol

```

It loads shitload of stuff, gives a small error wich it says is NP for X, and moves on and now comes the part I need help with:

```

err:module: import.dll Library DivxDecoder.dll (Wich is needed by L"C:\\windows\\system32\\Wow.exe") not found

err:module: Initialize Thunk Main exe initialization for L"C:\\windows\\system32\\Wow.exe" failed, status c0000135

waiting for X server to shutdown ddxSigGiveUp: closing log

XIO: fatal IO error 25(Inappropriate ioctl for device) on X server ":0.0"

after 573 requests (520 known processed) with 0 events remaining

```

And this is the nice little error that is keeping me away from playing World of Warcraft.

Is there anyway to fix this?
Just tell if anymore information is needed about my PC and it's settings.

Regards,
Zirts

---

### Post by MaximB on 2010-08-23
Problem finding the Wine section on UbuntuForums...Please Help !!!

---

### Post by Zirts on 2010-08-23
Kinda fits under games too as I'm tryng to start a game here...

---

### Post by del_diablo on 2010-08-23
> **err:module: import.dll Library DivxDecoder.dll**

What about this error message did you not see?

---

### Post by Perfect Storm on 2010-08-23
> **Zirts said:**
> Kinda fits under games too as I'm tryng to start a game here...

No it doesn't. Please read the game forum guidelines again. Thanks.


Thread closed.

---

