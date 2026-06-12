---
title: "Steam and ATI"
date: 2007-06-09
forum: Gaming &amp; Leisure
---

### Post by akschnare on 2007-06-09
Hey,
I'm fairly new to Linux and I want to run Steam on my system. I installed Wine and Steam, and I installed the proper Microsoft fonts. Now when I try to play Half Life, it tells me that my drivers are out of date and that I should update them. I ignore it and then it just slows down so much that it won't get past the initial valve logo screen. 

I'm current'y using the open source ATI driver and AIGLX. Previously I had the Radeon driver, but the desktop effects wouldn't work and when I installed Beryl, it really slowed down my computers performance.

So I guess my question is this, is there any way to run steam and maybe Starcraft eventually while using these open source drivers? 

If it helps, I'm running an Athalon 2500+ with a gig of ram and a Radeon 9600XT.

Thanks for any help.

Andrew


Edit: Is there also a way to run Enemy Territory with this driver? I was going to start that as well, and if there isn't then I won't bother. Thanks again!

---

### Post by Peetke on 2007-06-10
Did you get the latest Wine? And did you try to run the games in OpenGL mode? These will probably be a lot faster than the Direct3D/X mode.

---

### Post by akschnare on 2007-06-10
How do you run the game in OpenGL mode?

---

### Post by lordhebe on 2007-06-10
Half-life defaults to opengl mode, but if it's somehow set it'self on directx mode then use the -gl flag.

---

### Post by akschnare on 2007-06-10
Sorry for my ignorance, but how do I do that?

---

### Post by MenZa on 2007-06-10
Right click the Half-Life entry in Steam (or your launcher for it), and choose 'Properties'. Click the "Set Launch Options..." button and in the field, type *-gl*, then hit OK. (If you're doing it with a launcher, that could be e.g. wine "/home/user/.wine/drive_c/Program Files/Steam/Steam.exe -applaunch 70 -gl").

---

### Post by akschnare on 2007-06-10
Thanks. 

Although apparently that wasn't my problem as it still loads at 800x600 and then crashes just before the title menu.

---

### Post by jimminy_kriket on 2007-06-10
You will probably need fglrx

---

### Post by akschnare on 2007-06-11
Well thats not good news. Oh well, will I need it to run all games, or do you think I can still run older games as well? Like Enemy Territory or Starcraft?

---

### Post by BeardlessForeigner on 2007-06-11
I'm currently facing the same problem with Frets on Fire. However, I have 2 FPS's running, World of Padman and Tremulous, with the open source drivers and AIGLX (SInce XGL made my computer miserable)

---

### Post by akschnare on 2007-06-13
I guess its good to hear that others are having the same problem. At least it's not something that I'm doing wrong. Oh well, I'm sure I'll live.

---

