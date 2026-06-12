---
title: "ePSXE won´t find plugins (Wine)"
date: 2013-11-27
forum: Emulators
---

### Post by r-bonn on 2013-11-27
Hi there,
ive benn trying to get ePSXE to work, but i ran into problems with it. First off, this is my laptop: Lenovo Ideapad Y570 with Ubuntu 12.04 64 bit. It´s an optimus laptop with Intel HD 3000 and geforce GT555M graphic chip.I´ve been using bumblebee to switch between the graphic chips. I know that there´s an ePSXE version for Linux and PCSX in the softwarecenter. Those versions starting and runing on my laptop, but with some isseues. I can´t play all my games with epsxe for linux, because some copy protected games won´t load and with pcsx i have some graphic isseues. So i thought i try the Windows one with Wine. But there´s a problem i don´t understand. If i double click the exe, all is normal, all plugins are loaded, i can configure the plugins and play all games. Only thing is that the HD3000 is too slow. So i want to use my GT555M. I open the console try to open the exe with optirun or primusrun and this happened:
```
roland@roland-Lenovo-IdeaPad-Y570:~$ primusrun '/home/roland/Downloads/ePSXe.exe' 
 * Running ePSXe emulator version 1.9.4. 
 * Running ePSXe emulator version 1.9.4. 
not video plugins found


```
All boxes are empty, the plugins, bios, memory card could not load. Why? I don´t know if this problem is caused thru bumblebee or Wine. Iv´e been trying since week´s to find a solution, but nothing. Is anyone here with the same problems or can help me?

---

### Post by deadflowr on 2013-12-03
I had only got epsxe to work once, ever, and the performance was total garbage.

Pcsx has worked flawlessly for quite sometime, maybe since Oneric.
The trick is though, you need to get a real bios, and extra plugins.

A pcsx/psx forums can tell you how to do both.(or just google/search)

The pcsxr package that comes in the repos has a generic set of both a bios and plugins, but they are not very good.
I know there is a nice linux plugin package somewhere that you can download.
A bios is a different story, because there are legal issues with it.

---

