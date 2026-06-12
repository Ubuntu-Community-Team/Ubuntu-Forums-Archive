---
title: "ram"
date: 2006-05-28
forum: Desktop Environments
---

### Post by carterdea on 2006-05-28
my ubuntu laptop is very slow. I thought it worked on outdated computers? What gives? I have a 400mHtz PIII with 64mb RAM. It takes near 25 min. just to boot up. THanks,
carter

---

### Post by kostkon on 2006-05-28
The processor is OK, I think the problem lies in the low memory of 64MB. It is very important to have a decent amount of memory to get a good speed from Ubuntu. If you can increase the memory to 192 or 256MB, you'll see a increase in the perfomance. Generally a >=192MB is good enough.

A good solution for you is to try Xubuntu so the gui will not consume so much memory and leave some free for the rest of the processes.

---

### Post by Harleen on 2006-05-28
But it did work, right? Noone said, it would be fast. ;) 

Seriously: Your PC is busy with swapping. Your PC needs more RAM, the more, the better. But your subject indicates, that you already know that. 
If you cannot put in more memory, you can try out some slim window manager and turn off unneeded system services. But that will only make your computer to run faster, but not fast. I doubt that you will get a graphical system running smoothly with that configuration. But a server install should be possible - without any GUI.

---

### Post by kostkon on 2006-05-28
[QUOTE=Harleen]I doubt that you will get a graphical system running smoothly with that configuration. But a server install should be possible - without any GUI.[/QUOTE]

Come on Harleen, don't underestimate Ubuntu! It can run on a P3 400MHz fast enough with a good amount of memory or even a lighter gui -such as XFCE instead of Gnome- it's not a solution to get rid the whole of the gui...!!

---

### Post by Harleen on 2006-05-28
If carterdea's computer is already swapping on startup even a lighter window manager won't help that much. It would only reduce the amount of swapping. ;)
Even XFCE will be too much for only 64 MB. If you really want a GUI on this thing, I'd suggest fvwm, as it doesn't use either QT or GTK. But I still doubt it will be much fun working with this thing.

---

### Post by kostkon on 2006-05-28
Yeah I understand. With the current configuration the situation is bad. The OS is struggling, swapping all the time. 

If carterdea is able to increase the memory of the pc from 64MB to 192MB or more, I think he/she will be able to run Ubuntu with a decent speed.

---

### Post by jones_jj on 2006-05-29
First not to get nitpicky, but 400 MHz is not a PIII it's only a PII, the PIIIs began with 450 MHz, but most would say 500 MHz is the first true PIII :P

I run Ubuntu on a PII 400 MHz with 384 MB of RAM it runs just fine.  It just take a little bit of time, maybe 30-45 seconds to launch some applications but that's not really that long of a delay if you think about it.  I agree with kostkon, if carterdea just even doubles his/her RAM he/she would notice a huge difference.

---

### Post by Sukarn on 2006-05-30
I had a PIII 500 MHz with 64 MB RAM that I ran Ubuntu on before I installed it on my AMD Athlon XP 2400+ (~450 MB RAM)(I wonder whats gone wrong with my BIOS, saying that its AMD Athlon XP 1800+).
I got rid of the old CPU, so I can't try anything on the old thing anymore, but when I had it, it booted and ran Ubuntu quite fast. The boot time was about 2 minutes (till the log in screen, about 3 minutes including login by typing username, pass). I ran Gnome on it and some applications took longer to load (firefox took ~35 seconds to start).

---

### Post by az on 2006-05-30
[QUOTE=jones_jj]First not to get nitpicky, but 400 MHz is not a PIII it's only a PII, the PIIIs began with 450 MHz, but most would say 500 MHz is the first true PIII :P
[/QUOTE]


No, I have a 400 Mhz pIII in a box at home.  I have a 450 MHz one, too.

I have not found a pII that is faster than 400 MHz, though.


carterdea:  Does Ubuntu run slower than Windows XP on that box?

---

### Post by starfireview on 2006-05-30
I'm running a P2 450mh (which sounds close to what you are running). Things run fine, it takes at most two minutes for the original boot.

I think the big difference is the memory. I had 64Mb in it, and it ran Windows 98 slowly (but it did run it). I upgraded another 128Mb a while ago (i've just switched to ubuntu) and mine is working fine. So I've got the 192 Mb that people here seem to think would work (but just barely).

My machine is running faster on Ubuntu than on Windows...guess it depends.

I managed to find the 128Mb piece for $30CAN used from a shop in town:) ....I took me a while to find the shop (some were charging quite a bit more), maybe i could help with how i managed to find it? It was easier to pay $5 for a used network card then figure out why mine wouldn't work (i'm on an old cranky IBM that tends to proprietary...it didn't like the first piece of memory i got it!).

Now if only i could get my sound card working...
Starfireview

---

### Post by jones_jj on 2006-05-30
Good old Intel saying one thing and meaning another.  I have always seen PII stopped with 400 MHz and a few 450 MHz and then PIII start with 450 MHz and 500 MHz.

Windows XP will be very slow with all the pretty turned on with only 64 MB of RAM.  You will need to run XP in the 2000 style desktop for it to run decent with 64 MB.

---

### Post by az on 2006-05-30
[QUOTE=starfireview]Now if only i could get my sound card working...
[/QUOTE]
[https://wiki.ubuntu.com/HowToSetupSoundCards](https://wiki.ubuntu.com/HowToSetupSoundCards)

---

