---
title: "Quake 4 crashes on startup - changed sdl library and still broken"
date: 2006-06-14
forum: Gaming &amp; Leisure
---

### Post by ironfistchamp on 2006-06-14
I installed Quake 4 and it ran first time from the installer. Then when I ran it a second time (to fix the sound) it flashed on screen and then died. The mouse messsed up too so I had to restart gdm. I tried again this time changing the sdl library from libsdldebian-all to libsdldebian-oss. That didn't work so I tried the alsa one aswell. That didn't work either.

What is going on. I can only get it to run by reinstalling it.

Any help appreciated

Thanks

Ironfistchamp

---

### Post by ironfistchamp on 2006-06-14
Ok just fixed that problem. Running as root seemed to do the trick. Next problem is when I start a new game it starts loading and then comes back to the main menu. The console output is

  ERROR: Joint 'chest' not found for 'joint_head' on 'ad_intro_char_marine_3'

How can I fix this? Does anyone know?

Thanks

Ironfistchamp

---

### Post by Perfect Storm on 2006-06-14
Well, this is a guess (as I don't have Quake 4). Did you install Quake 4 with sudo sh /blah/blah/blah... and afterwards hit the run the Quake 4 button?

---

### Post by ironfistchamp on 2006-06-15
Yeh that is how I did it. That's right isnt it?

There is alot of warnings about models. Could it be that that pak files are corrupted or something and it can't find certain parts?

I may try re-copying the files over if I can find my disk.

Ironfistchamp

---

### Post by FredB on 2006-06-15
[QUOTE=ironfistchamp]Yeh that is how I did it. That's right isnt it?

There is alot of warnings about models. Could it be that that pak files are corrupted or something and it can't find certain parts?

I may try re-copying the files over if I can find my disk.

Ironfistchamp[/QUOTE]

It would help. I finished it - not too bad, and waiting for a expansion pack - and no problem playing it, even if it was in 640x480 in medium details.

But I don't have too much money to buy a Nvidia GeForce 6600 GT :(

---

### Post by ironfistchamp on 2006-06-15
My brother got a 6600GT for £60 from ebuyer. If you play gmaes alot then I suggest something a little bit more powerful. I mean its good but for gaming that bit extra makes all the difference.... 6800?

I spent £320 on a 7800 GTX and I am loving every minute of my gaming. It plays practically everything I throw at it on full.

---

### Post by FredB on 2006-06-15
[QUOTE=ironfistchamp]My brother got a 6600GT for £60 from ebuyer. If you play gmaes alot then I suggest something a little bit more powerful. I mean its good but for gaming that bit extra makes all the difference.... 6800?[/quote]

60 pounds ? So around 80 euros ? PCI Express ? Because I have an old (3 years old) Pentium 4 based computer. Only AGP for me.

> 
I spent £320 on a 7800 GTX and I am loving every minute of my gaming. It plays practically everything I throw at it on full.

320 pounds ? I am not that hardcore gamer though ;)

---

### Post by Perfect Storm on 2006-06-15
[QUOTE=ironfistchamp]Yeh that is how I did it. That's right isnt it?

There is alot of warnings about models. Could it be that that pak files are corrupted or something and it can't find certain parts?

I may try re-copying the files over if I can find my disk.

Ironfistchamp[/QUOTE]

Nope, if you push thestart Quake button right after you install it, you properly run into permission problems which could be a reason for the errors. When installed then exit thereafter start Quake up. If you wanna try a new install, get rid off .quake4 in your home folder.

---

### Post by ironfistchamp on 2006-06-15
FredB the card he got was AGPx8...it was a present from me and there was no way I was rebuilding his computer just for PCI-E. Anyway he only plays Oblivion and Guild Wars (still a windoze fan boy). It worked out a little more than 60 due to PnP but still pretty damn good.

AI well I''ll be jiggered that did the trick. We certainly have some bright sparks here. :D 

Thanks
 Ironfistchamp

---

### Post by Perfect Storm on 2006-06-15
> well I''ll be jiggered...

Irish man? ;)

---

### Post by FredB on 2006-06-15
> **ironfistchamp]FredB the card he got was AGPx8...it was a present from me and there was no way I was rebuilding his computer just for PCI-E. Anyway he only plays Oblivion and Guild Wars (still a windoze fan boy). It worked out a little more than 60 due to PnP but still pretty damn good.:[/quote]

I can imagine. But as I am an old school FPS player (no, not talking about the *bip* called Half Life), a GeForce FX 5200 is the best for me  said:**
> 
AI well I''ll be jiggered that did the trick. We certainly have some bright sparks here. :D 

Thanks
 Ironfistchamp

:cool:

---

### Post by ironfistchamp on 2006-06-15
Hehe I'm not Irish I just tried to be polite. Ill be jiggered is nicer than saying "Well I'll be f**kd" :p

---

