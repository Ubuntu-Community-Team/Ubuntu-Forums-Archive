---
title: "Playstation 3 and linux!"
date: 2008-12-13
forum: Gaming &amp; Leisure
---

### Post by emshains on 2008-12-13
So, I am planning to buy a gaming console. Since I have a HD tv, and I only have one choise- PS3. *I won't support microsoft with xbox, and Wii is too underpowered*

So, since PS3 was able to run other unix oses, I tried to find out which would suit me better. So, ubuntu has a distro with a modified ppc kernel, which supports Cell better, but the thing is, it doesn't really use its potential, it only uses the ppc unit, which is meant for feeding data to the cell, I may be mistaking the "fact" stated above, but the idea is, that the kernel isn't really using the cell. I don't really know about the Yellow Dog Linux, because their website only says that it is now using E17, nothing about a kernel that would actually use the cell. 

Since my father is pretty experienced with linux, he said he could compile everything from source. Ok, it would be quite hard, but then the system would just FLY! 
Then again, since PS3 has a nVidia gpu, we would need a driver for it, but since nVidia's drivers are all closed source, there really is no way to use proprietary drivers, we should use an open-source one. Could you tell me, which one is the most advanced open source nvidia driver today ? Well, I am not going to play any GL games, but I'd want to watch some video, maybe some occasional gaming. 

And is it even possible to compile the linux kernel, so it would use all the h/w of the PS3 ? Or am I better off with a kernel that just work?

---

### Post by viciouslime on 2008-12-13
I'm pretty sure the PPC build of ubuntu will use the cell to its full potential. As far as I am aware it i just an 8core PPC processor so if SMP is enabled, which it will be, then you will be using the cell to the best of its ability.

However, the nvidia GPU doesn't only require a driver, but would require some serious messing around with the inside of your PS3 and as far as I'm aware no one has managed that yet. Sony have deliberately stopped the 3d acceleration potential of the GPU from being accessible by anything other than the PS3's own OS. Presumeably this is to stop people buying a PS3 at sony's expense and then not buying any games for it, but instead running linux games on it.

---

### Post by emshains on 2008-12-13
> **viciouslime said:**
> I'm pretty sure the PPC build of ubuntu will use the cell to its full potential. As far as I am aware it i just an 8core PPC processor so if SMP is enabled, which it will be, then you will be using the cell to the best of its ability.

However, the nvidia GPU doesn't only require a driver, but would require some serious messing around with the inside of your PS3 and as far as I'm aware no one has managed that yet. Sony have deliberately stopped the 3d acceleration potential of the GPU from being accessible by anything other than the PS3's own OS. Presumeably this is to stop people buying a PS3 at sony's expense and then not buying any games for it, but instead running linux games on it.



Nope, the cell has another ppc processor "in front" of it, as I said, to manage the cell. So the multi-threading abilities of cell aren't used, which is a waste. But, could I be able to watch HD with the drivers that are already there?

---

### Post by Izek on 2008-12-13
Tried Yellow Dog Linux?

[http://us.fixstars.com/products/ydl/](http://us.fixstars.com/products/ydl/)

(In case you didn't realize, I was joking.)

---

### Post by maddog46113 on 2008-12-13
This site may help you.

[http://psubuntu.com/](http://psubuntu.com/)

The PS3 can run intrepid.

---

### Post by emshains on 2008-12-14
Of course it can run interpid, in fact, it can run any kind of linux distribution, that is compiled for ppc. But that isn't making it use the cell.

---

### Post by 10011010 on 2008-12-14
I'm not sure what level of the cell you wish to dig into, it is still physcially a triple core proc.  The 8 cores are software based.  I have read multiple reputable sources that say it uses a hard coded hypervisor to restrict access to the RSX but Sony openly provides all APIs -- so a mesa driver should work fine for 2D.  Without multimedia enhancements, you'd really have nothing else to dig into on the cell.  The ps3 is good to have a nice code crunching box, though I'd suggest Xubuntu -- since you are limited to 256 MB RAM.

---

### Post by emshains on 2008-12-15
> **10011010 said:**
> I'm not sure what level of the cell you wish to dig into, it is still physcially a triple core proc.  The 8 cores are software based.  I have read multiple reputable sources that say it uses a hard coded hypervisor to restrict access to the RSX but Sony openly provides all APIs -- so a mesa driver should work fine for 2D.  Without multimedia enhancements, you'd really have nothing else to dig into on the cell.  The ps3 is good to have a nice code crunching box, though I'd suggest Xubuntu -- since you are limited to 256 MB RAM.


Since I am not going to do anything besides the basics on it, I won't need a deb system, nor will I need xfce. I rather go with YDG.

---

### Post by roelpeeters on 2008-12-15
> **10011010 said:**
> I'm not sure what level of the cell you wish to dig into, it is still physcially a triple core proc.  The 8 cores are software based.  I have read multiple reputable sources that say it uses a hard coded hypervisor to restrict access to the RSX but Sony openly provides all APIs -- so a mesa driver should work fine for 2D.  Without multimedia enhancements, you'd really have nothing else to dig into on the cell.  The ps3 is good to have a nice code crunching box, though I'd suggest Xubuntu -- since you are limited to 256 MB RAM.
Actually the 8 SPEs are physical units that you can recognize on the die (google for a picture of the CELL processor). Sony has limited the number of SPEs available to 7, the other one is used for the hypervisor itself. The XBOX360 has also an IBM processor which is a triple-core processor, but both processors are completely different beasts and have nothing to do with eachother.
The graphical chip (RSX) has been limited by Sony, and the graphical drivers the open source community are developing, are based on the use of the SPE(s).

---

