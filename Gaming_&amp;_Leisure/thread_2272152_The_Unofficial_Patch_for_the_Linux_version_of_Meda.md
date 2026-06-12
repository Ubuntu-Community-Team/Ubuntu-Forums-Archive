---
title: "The Unofficial Patch for the Linux version of Medal of Honor"
date: 2015-04-04
forum: Gaming &amp; Leisure
---

### Post by mateo14 on 2015-04-04
Hi

Someone created the unofficial patch for the Linux version of Medal of Honor

"Hello everyone, I wanted to tell you what I did to run the game Medal of Honor. Allied Assault (Mohaa) Linux This game is supposed to work with wine, but unfortunately I could not go further the installation and after a bit stressed whether with wine or Crossover Games, I gave up and I turned to a more or less official port of the game on Linux: [http://icculus.org/~ravage](http://icculus.org/~ravage) / mohaa / So this installer is downloaded, it is launched, nothing happens - it decompresses the "self extract", we finally found the setup.gtk binary installer and the installation runs about normally from there. The game starts and works much ... The sound is still bad, we not hear the dialogues, there is the sound from the left speaker, but it's still playable. Except that passed the first mission, things go wrong. The game freeze completely in three steps. But I really wanted to play this game! Luckily binaries are distributed with (some) debug symbols, so launch the game in gdb gives results pretty near readable, which facilitates disassembly. I spend the game in windowed mode, I disable the "grab" the mouse pointer (so you can type commands gdb after the crash happened) and I reproduce the crash. It this is a segfault - I did not keep a copy of the backtrace, but the function where the crash occurs is called void ClientGameCommandManager :: PlaySound (str *, float, int, float, float, float , int) and is at 0x0004b0f0 . So I came out the big guns, namely objdump -d, to disassemble the function, and since the sound was walking anyway not so great, I thought I would pass me completely. You should know that the sound is not switched off in Mohaa: you can turn the volume down, but that's it - which of course did not prevent the crash from occurring. Here the beginning of the function, it is a classic prologue x86 function: 
0004b0f0 <_ZN24ClientGameCommandManager9PlaySoundE3strPfifffi>: 
4b0f0: 55 push% ebp 
4b0f1 89 e5 mov% esp,% ebp 
4b0f3: 57 push% edi 
4b0f4 56 push % esi 
4b0f5 53% ebx push 
4b0f6 83 ec 4c sub $ 0x4c,% esp 
4b0f9: c7 dc 45 00 00 00 00 movl $ 0x0, -0x24 (% ebp) 
4b100: 3d 80 40 26 00 00 a1 CMPB $ 0x0 , 0x26a140 
4b107: 0f 84 53 04 00 00 I 4b560 <_ZN24ClientGameCommandManager9PlaySoundE3strPfifffi + 0x470> A very simple way to prevent the crash, is to prevent this function to run - the simplest solution is to put a "ret" (return) at the beginning of the prologue. A coup d'hex editor and we get: 
4b0f0: c3 ret 
4b0f1 89 e5 mov% esp,% ebp 
4b0f3: 57 push% edi 
4b0f4 56% esi push 
4b0f5 53% ebx push ... what makes ample case. After restarting the game, plus there is no sound, and no more crash is reported. This is the second time in my life I'm doing a patch directly on a bit to fix a bug (again it was on the Intel DRI driver to fix a crash on my EeePC without recompiling everything), and overall it's pretty simple. For cons, the lack of debug symbols would have been a problem as not having the name of the function (PlaySound) would not have allowed me to know that it was the sound. I then could not have had such an aggressive approach to bypass the crash. I was able to play for two hours before encountering bugs in the port of the virtual machine running mission scripting, so I stuck on a mission. But that's another story! :) Voila, I hope it makes you want to those who have the Mohaa CD in a corner to reinstall the game as their favorite OS!" 

[http://linuxfr.org/users/ahuillet/journaux/patch-de-binaire-pour-faire-tourner-medal-of-honor-allied-assau](http://linuxfr.org/users/ahuillet/journaux/patch-de-binaire-pour-faire-tourner-medal-of-honor-allied-assau)

I finished this game in 2005/2006 on Debian Sarge.
In my case, the game will start to crash in this location on my old PC or Mac with every Linux distribution based on kernel 2.6, 3.0 etc:


[https://www.youtube.com/watch?v=gkLKYipiPlA](https://www.youtube.com/watch?v=gkLKYipiPlA) 


2:43


I know that this game is playable on Debian stable (sarge) with Linux 2.4, and Linux 2.6 but not higher than 2.6.7.

I suspect that this game is playable on every distribution with Linux 2.4, but I do not have the access to my old PC, and it is impossible to run this game on the virtual machine e.g. VMware, Virtualbox. 

This person discovered the issue, and he probably found a partial solution. I do not know two things about this game. Why could I play in this game without issues on Debian stable with kernel 2.4? What changes have been made in Debian with Linux kernel higher than 2.6.7? That will probably help to find the source of this issue with the game.

I am wondering if the game will not be crashing with the sound turned on in the other levels if I will use this hack to save the game after this location where the game crashes.

Can you help me? I do not know how to use this patch.

---

