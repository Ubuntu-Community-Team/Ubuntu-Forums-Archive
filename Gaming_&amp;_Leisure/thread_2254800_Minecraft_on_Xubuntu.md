---
title: "Minecraft on Xubuntu"
date: 2014-11-30
forum: Gaming &amp; Leisure
---

### Post by ramn2 on 2014-11-30
Hello, all
I have just switched from XP to Xubuntu 14.04.1 LTS. I could install Minecraft but it runs very slowly. My sistem specifications are:

2x Pentium (R) 4 CPU 2.80GHz
2 GB RAM
NVIDIA GEFORCE FX 5200

Is it worth installing more RAM? 

Thanks

(Sorry for my english)

Ramon

---

### Post by SirMoo on 2014-11-30
> **ramn2 said:**
> 
Is it worth installing more RAM? 


Yes. It's playable with out more... But your OS will use a bit of the ram... And Minecraft tends to be ram hungry. Try to go for 4-6 GB... Makes things nicer.

---

### Post by Dragonbite on 2014-12-03
The RAM looks like you're biggest weak point.

My dual-core laptop does alright with settings down to near minimal and with 4 GB of RAM.  I get about 10-30 fps (you can tell the fps by hitting F3 during the game).

So I agree, get 4 or more GB of RAM installed.  In general, if I can afford it I would max out the RAM because it is the biggest boost for older systems and will keep your system usable longer.

---

### Post by dannyboy79 on 2014-12-03
YES, more RAM! :)

---

### Post by irongolem0982 on 2014-12-03
I run minecraft on 2 GB of RAM with no problems, you can see how much  ram minecraft uses in the game, just press f3 and look for "Mem" in the  upper right hand corner. my guess is that RAM is NOT your bottleneck. I  would guess it is your CPU. personally i have had the same 2x Pentium  (R) 4 CPU 2.80GHz on xubuntu and my luck with minecraft on it is about  the same as yours. i get like 12fps and sound crackling. when i switched  to my lubuntu boot all that goes away after 1-2 minutes and i get  60+fps. maybe it is how it handles java?

hope i helped!

---

### Post by Dragonbite on 2014-12-04
Are you using Oracle's Java, or OpenJDK?

---

### Post by mastablasta on 2014-12-04
you can set the amount it is using. I set mine on 512 MB and is running just fine. the "client" has 1,2 GB ram and Kubuntu installed. working juts fine though sometimes view distance is not that far

---

### Post by ramn2 on 2014-12-04
Thank you all for answering

Minecraft uses 500 mb (=mem press F3) and 1 or 2 fp (I don’t know what does this mean). I use OpenJDK. As you can guess, I’m a complete newbie

I would appreciate your comments. Thank you

---

### Post by SirMoo on 2014-12-04
Try Oracle Java and see if you get better results.

---

### Post by mastablasta on 2014-12-05
how much ram does NVIDIA GEFORCE FX 5200 have? does the card have full openGL support or is it on opersource drivers?

this setup should run it fine. not super fast, but very playable.

you have to limit your ram usage with command line. as otherwise it just starts to consume more and more until it starts disk swapping for memory and that's when the slow down will occur.

for windows but same commands apply to Linux: [http://www.wikihow.com/Allocate-More-RAM-to-Minecraft](http://www.wikihow.com/Allocate-More-RAM-to-Minecraft)

you should allocate it 1 GB ram. and I hope that GPU card of yours has at least 256MBram. otherwise you might need different tweaks.

---

### Post by ramn2 on 2014-12-05
I switched to Oracle Java 8. NVIDIA GEFORCE FX 5200 have 128MB, I guess.  I allocated 1 GB RAM to Minecraft. But none of these worked, it keeps  running very slow. Thank you for answering

---

### Post by mörgæs on 2014-12-05
I suggest that you initially set all video options in Minecraft to the lowest value for comparison. It makes a big difference. 

After that you can increase some of them step by step to see if you get a useable result.

---

### Post by Dragonbite on 2014-12-06
> **mörgæs said:**
> I suggest that you initially set all video options in Minecraft to the lowest value for comparison. It makes a big difference. 

After that you can increase some of them step by step to see if you get a useable result.

And do the changes via the Options before you go into a world. It makes a big difference.

---

### Post by mastablasta on 2014-12-07
then again it could be the GPU. I have similar computer as Kubutnu PC, only slightly less ram (only 1 GB) and weaker GPU (128MB rather than 256MB)) and i tried mientest on it and it barely ran even on fully minimum settings. as a bonus it seems the GPU didn't have good drivers support (anymore) and the CPU took on all the weight.

---

