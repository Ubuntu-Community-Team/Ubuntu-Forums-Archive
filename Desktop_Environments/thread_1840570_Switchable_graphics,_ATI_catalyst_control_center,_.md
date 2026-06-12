---
title: "Switchable graphics, ATI catalyst control center, etc, etc..."
date: 2011-09-07
forum: Desktop Environments
---

### Post by MG2R on 2011-09-07
I know the interwebs are full of Q&A about this topic, but I haven't been able to find a definitive solution to my problem:

I'm trying to run Ubuntu instead of Windows 7 on my brand new Dell Votro 3350. The Vostro has an intel core i5 with built in HD Graphics 3000. On top of that, the Vostro has an AMD/ATI HD6490M GPU.

In windows, switchable graphics work seamlesly, in Ubuntu however, they do not!

I tried installing the catalyst control center, but once installed, I get an error message that I can't run Unity anymore (which actually is not that bad, I prefer Gnome anyways). When I try to enter the control center, it gives me an error telling me that there is no AMD/ATI GPU found in the system!

I've also tried installing the fglrx driver on it's own, through the terminal without a great deal of succes.

Can anyone please help me out on this one? I'm sick of using Windows!

---

### Post by MG2R on 2011-09-09
Realy? No one? :(

---

### Post by Leopardson on 2011-09-11
It seems that a lot of us have questions and nobody seems to have answers. I have the same problem - Switchable graphics with no way to switch.

---

### Post by qwertyas on 2011-09-13
I still have the same kind of problems. See my older messages - no solution yet.
I'm curious if other distributions deal better with this issue.

---

### Post by SeijiSensei on 2011-09-13
[http://linux-hybrid-graphics.blogspot.com/](http://linux-hybrid-graphics.blogspot.com/)

---

### Post by iofthestorm on 2011-09-25
I swear that at one time, on 10.10 with Catalys 11.6 I had switchable graphics working for about a month, but something weird was happening so I tried to upgrade to 11.8 and since then I haven't been able to get it to work. I even tried reinstalling and then installing 11.6 to no avail. I'm on Ubuntu 11.04 right now though, gonna try installing 11.10 beta on another partition and also 10.04 and see if any combination of Ubuntu/Catalyst works. I've got an Envy 14 with Intel HD graphics and Radeon 5650, it's the same problem more or less. I've heard that newer graphics cards have an option in the BIOS to choose one or the other which might work. Mine has the option but it gets reset on every boot so it's not terribly useful, and you have to use some stupid button mashing to get into the advanced BIOS instead of the normal one.

---

### Post by MG2R on 2011-09-26
Keep us updated on how your progress goes ;)

---

### Post by qwertyas on 2011-11-27
The same problem, with the same laptop dell vostro 3350 I5,hybrid graphics, dual boot (win7 and linux).
I can't make the dual graphic working, although the Intel graphic deals ok with most tasks.
Is your fingerprint working?
Have you updated the bios of you laptop (v. 07 on dell's site)?

---

### Post by MG2R on 2011-11-27
Got it working, but stopped using Ubuntu because of the **aweful** Unity! I can not see how anyone can find that better than Gnome 2... Gnome 3 rather sucks too -_-

Anyways, if you want to try it for yourself: [https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)
I used a CLEAN INSTALL (no drivers whatsoever) en just followed the instructions above... It took me 3 formats and reinstalls to get it working.

---

### Post by qwertyas on 2011-11-29
> **MG2R said:**
> 

Anyways, if you want to try it for yourself: [https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)
I used a CLEAN INSTALL (no drivers whatsoever) en just followed the instructions above... It took me 3 formats and reinstalls to get it working.

OMG, you couldn't have been more dissuasive than that! Only 3 formats and reinstalls?

---

### Post by typhoon_tip on 2011-11-29
FGLRX does NOT support switchable graphics. You have several options:

- You want to use switchable graphic: use the stock ATI driver and Intel driver (all loaded by default) and install the script to switch between cards.

- You want to use 3D and OpenGL acceleration of FGLRX: fix the BIOS setting to use only Discrete card (always on Discrete) and install FGLRX. The problems you are lamenting should disappear totally.

---

### Post by Milos_SD on 2011-11-29
FGLRX DOES support switchable graphics, but you have to restart X or your PC. It worked out of the box on SLED 11 that was installed by default on HP ProBook 4530s. But on Ubuntu it gives me X segfault. :( It most be something with Ubuntu's implementation of Xserver. :)

---

### Post by Haventfoundme on 2011-12-20
Just moved from fedora 16 to Ubuntu 11.10. I have a HP dv7 4285dx and I haven't found a solution to the discrete graphics debacle. Nevertheless this is a bigger problem across all linux distros because Mint and Debian don't even have simple solutions to this issue. 
Just a daily complaint and some FYI.

---

