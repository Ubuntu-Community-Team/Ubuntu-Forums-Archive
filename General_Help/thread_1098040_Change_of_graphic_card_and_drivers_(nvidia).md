---
title: "Change of graphic card and drivers (nvidia)"
date: 2009-03-16
forum: General Help
---

### Post by ene_dene on 2009-03-16
I used a card nvidia 8600GT, I used the newest nvidia drivers from their site 180.22 and they worked just fine. I needed these drivers for CUDA computing.
I decided to upgrade card, so I bought 9800GTX+ and replaced the card. Nvidia X Server Settings showed the new card and it seemed that it worked fine. However, I couldn't use CUDA, and then I started testing the card in 3d games. Nexuiz didn't run smoothly, it did count a good frame rate, but when turning around you could notice it was not good as it should be.
Then I removed the drivers, and installed the default ubuntu 8.10 drivers, but the same thing.
Does anyone have a clue, what could it be and how to fix it?

---

### Post by TenPlus1 on 2009-03-16
You could try running the nvidia-settings and turnond 3D vsyns ON...  this limits the frame rate to your monitor's refresh rate and gives you a much smoother 3d performance using less cpu power...

---

### Post by Zmrlzna on 2009-03-16
I've changed my graphic card recently to a nvidia 9500GT and after some problems I've finally managed to make it work installing drivers with EnvyNG. Try with it:

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by ene_dene on 2009-03-16
> **TenPlus1]You could try running the nvidia-settings and turnond 3D vsyns ON... this limits the frame rate to your monitor's refresh rate and gives you a much smoother 3d performance using less cpu power...[/QUOTE]
Thanks, but that doesn't seem to be the problem. The problem is that it looks though sometimes the framerate drops too low, although the counter shows differently. It shouldn't happen, because with a older card id didn't happend. 

[QUOTE=Zmrlzna said:**
> I've changed my graphic card recently to a nvidia 9500GT and after some problems I've finally managed to make it work installing drivers with EnvyNG. Try with it:

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Is there a gnome GUI interface for this program maybe?

Edit: OK, I've found the answer to my question. Thank you.

---

### Post by kelvin spratt on 2009-03-16
Not all the Nvidia cards are good I have 1 of the gamers cards  8000 series 1gb of ram built in but it does not work with any Kernel after 2.6.25 nor windows7 but my 7600GS 512mb ram works perfect even with Compiz + transparency and anything else thrown at it with the latest drivers,  always check compatibility 1st

---

