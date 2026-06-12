---
title: "steam update 26% Problem"
date: 2007-09-10
forum: Gaming &amp; Leisure
---

### Post by KushMaster on 2007-09-10
I have wine 9.44 and i installed steam.exe from steampowered.com , my problem is when it is updating, it reaches 26% and it stops, and a window pops up and says. " steam is already running, You may only run one copy of steam at a time" Then i click ok and wine closes.  Can anyone please tell me how to resolve this problem ?

---

### Post by cogadh on 2007-09-10
Run it like this:
```
nice -n 19 wine steamTmp.exe SelfUpdate "Steam.exe" 14
```

---

### Post by KushMaster on 2007-09-11
Thanks for the code, but i tryed that same code that i got from a diff post and it didn't work, and i found a simmilar one that did work for me. Now i got a diff problem, I can't read what im clicking on when i use steam, ther is a window but not font, and my other problem is that i can't run counter-strike source because i need to enable openGL. How do i do that ?

Code i used in terminal to surpas the 26% problem is:

wine "C:\Program Files\Steam\SteamTmp.exe" Selfupdate "C:\Program Files\Steam\Steam.exe" 14

---

### Post by cogadh on 2007-09-11
That's essentially the same code, I just assumed that you had already changed directories to the Steam install directory. The one you used didn't require changing diirectories. Glad to hear it worked though.

As for your font problem, you need to copy the Tahoma font into Wine's font directory (~/.wine/drive_c/windows/fonts). If you have a Windows install, just copy it from there, otherwise do a Google search for it, I'm pretty sure you can download it.

The OpenGL issue is a function of your video drivers. If you have not already installed the accelerated driver for your video card, you will need to before most games will work correctly.

---

### Post by KushMaster on 2007-09-11
My friend installed my video card driver when he installed Ubuntu Feisty Fawn 7.04 OS, so im unsure as to how exactly im supposed to enable the OpenGL function on my video card. As to the Font problem, I did exactly what you told me to do and it didnt work, i D/L a package with alot of diff fonts including Tahoma, i put it in my Fonts folder for .wine/drive_c/windows/fonts and it still did not work, i also tryed some of the other fonts that came with the package and they didn't work either, I am a begginer at this stuff, so i need detailed step by step instructions on how to do this. Pleeease. Thank You.

Video Card: ATI Radion 1300X

---

### Post by KushMaster on 2007-09-11
I just read a thread about new ATI driver coming out this week. ( ATI 8.41 ). Might this update fix the OpenGL problem i get when i try to run CSS ?

---

### Post by cogadh on 2007-09-11
Not sure, I try to steer clear of ATI, too many issues in Linux. I'll let someone else take that one.

On the font thing, what format was the package you downloaded (.zip, .exe, etc.)?

---

### Post by KushMaster on 2007-09-11
Unfortunately I do not recall the format it was in. Why? Is there a specific format it is supposed to be in ?

---

