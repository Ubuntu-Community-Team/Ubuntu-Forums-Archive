---
title: "movies slowdowns"
date: 2006-06-15
forum: Desktop Environments
---

### Post by Marcelino on 2006-06-15
I recently installed Ubuntu 6.06 Dapper. I installed Multimedia Codecs with Automatix, but when I'm watching a movie I noticed that the CPU is used 100%, no matter what player I use: Xine, VLC or Totem.
When other processes are runing in background (for example downloading), the players are  losing a lot framerates.

What could be wrong? I mention that on the previous Ubuntu version, Breezy, I didn't have this problem.

---

### Post by BitTorrentBuddha on 2006-06-15
I had this problem as well, the only fix I could find was buying a new graphics card, I was (and I assume you are) using integrated video, correct? I think dapper taxes graphics much more heavily than previous installs, not even a theme change to legacy human fixed mine. The new graphics card is definitely worth it though, I would highly recommend buying one capable of running XGL/Compiz, it is indeed *the* sexiness.

---

### Post by Sukarn on 2006-06-15
I have the same problem on my system and my father is not going to get me a new graphics card.
XGL/Compiz is great, but if I use any effects, it hogs my graphics card.
By the way, I am using an integrated Nvidia GeForce 4 MX 440.

---

### Post by Marcelino on 2006-06-16
My graphics card is a Nvidia Geforce MX 440 to. But it is not integrated. What it is XGL/Compiz ?

---

### Post by coe on 2006-06-16
Yes, I experienced the same, to the point where it makes ubuntu unusable.
I wrote about it here:
[http://www.ubuntuforums.org/showthread.php?t=194814]("http://www.ubuntuforums.org/showthread.php?t=194814")

I installed fluxbox to see if a lighter window manager would somehow solve the problem, but no cigar. Which brings me to my original hypothesis that the upgrade from Breezy to Dapper basically just borked my setup... :( 
coe.

---

### Post by Marcelino on 2006-06-16
Coe, I saw your thread... It seems that I will need to install both Breezy and Dapper to take advantages of both :)).

---

### Post by BitTorrentBuddha on 2006-06-16
[QUOTE=coe]... Which brings me to my original hypothesis that the upgrade from Breezy to Dapper basically just borked my setup...[/QUOTE]
This isn't the upgrade, a fresh install still played movies poorly on my integrated card (when they worked fine under breezy.)
[quote=marcelino]... What it is XGL/Compiz ?[/quote]
Compiz is an alternative window decorator to metacity, it's pretty amazing as far as looks go, a search on youtube will produce plenty of examples. XGL is an X architecture that essentially just puts modern graphics cards' OpenGL to good use.

---

### Post by Marcelino on 2006-06-17
BitTorrentBuddha, can I switch back (downgrade) to... older alternatives of XGL/Compiz ?

---

### Post by BitTorrentBuddha on 2006-06-17
Chances are you aren't running XGL/Compiz, it isn't installed by default. And a downgrade would be unlikely seeing as it was just released in January I believe.

---

### Post by s_p_a_r_k_y on 2006-06-17
have you guys tried changing your output plugin? When I use fglrx I turn on the gl output driver, but if I boot wihtout it, then I use Xv as my radeon driver can't handle accelerated graphics. In gmplayer you can change it by right clicking going to preferences. Sure you can do it in xine too.

---

### Post by s_p_a_r_k_y on 2006-06-17
have you guys tried changing your output plugin? When I use fglrx I turn on the gl output driver, but if I boot wihtout it, then I use Xv as my radeon driver can't handle accelerated graphics. In gmplayer you can change it by right clicking going to preferences. Sure you can do it in xine too.

---

### Post by Marcelino on 2006-06-17
I have a Nvidia video card, so I don't know if I could try fglrx... Anyway, I will try switching the output driver Monday, because I will not be able until then.
Thanks, anyway :).

---

### Post by Marcelino on 2006-06-19
I have installed the Nvidia drivers, from [www.nvidia.com](www.nvidia.com). I have tried several output plugins, but still with no result. Ok, I give up for the moment... Anyway, I don't think is video card's fault.

Thanks for trying to help me ;).

---

### Post by Lord Illidan on 2006-06-19
Have you got DMA enabled?

---

### Post by Marcelino on 2006-06-20
[QUOTE=Lord Illidan]Have you got DMA enabled?[/QUOTE]
The DMA is enabled by default... I think.

---

