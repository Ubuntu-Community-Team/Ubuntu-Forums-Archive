---
title: "Is it possible that beryl causes the video card overheated?"
date: 2007-07-26
forum: Desktop Effects &amp; Customization
---

### Post by Gan Quan on 2007-07-26
hi,
I just installed beryl + emerald on my new dell d630, it runs smooth for around 10 minutes, then my system halt without any indications. I rebooted several times, and the problem reoccurred each time. I don't know if it's a software or hardware problem, but the center area of my laptop's bottom is really hot, and my system never crash if I turned beryl off. I suspect it's because the video card was overheated, but I'm not sure about it, is d630's video card placed at the center of the it's bottom? is there a solution to this problem? I really don't want to say goodbye to beryl :(

here is my software/hardware configuration: Feisty Fawn, nvidia driver version 100.14.11, beryl + emerald from official ubuntu repository; my video card is nvidia NVS 135M.

---

### Post by tbroderick on 2007-07-26
I would stop using beryl if I were you.

---

### Post by Gan Quan on 2007-07-26
> **tbroderick said:**
> I would stop using beryl if I were you.
My problem is, if this is caused by beryl (software), then there must be a way to solve it; if this is caused by my video card, then this is a serious hardware flaw, and I can't run any program demands intense 3d acceleration...

---

### Post by Franz1234 on 2007-07-26
As first step I would go to dell and ask them to check the Laptop. I had overheating problems with mine too but Acer replaced some parts. I collected the Laptop on the next day and everything was running great.

As second step I would install Compiz Fusion because in my opinion much better then Beryl and Its very stable already.


Good Luck :)

---

### Post by Gan Quan on 2007-07-26
> **Franz1234 said:**
> As first step I would go to dell and ask them to check the Laptop. I had overheating problems with mine too but Acer replaced some parts. I collected the Laptop on the next day and everything was running great.

As second step I would install Compiz Fusion because in my opinion much better then Beryl and Its very stable already.


Good Luck :)

Hi Franz1234, I will contact dell, but I'm afraid they would say this model is designed for windows, anyway, I'll give it a try later today. And thanks for the input about Compiz Fusion, I'll definitely try it later, I don't know this package before.

---

### Post by eentonig on 2007-07-26
And I would check if your laptop has fans that aren't working.

---

### Post by atomkarinca on 2007-07-26
i don't think beryl causes that much heat. i'm using beryl right now and my video card's fan is broken but i don't get any overheat. the problem is most probably caused by the hardware.

---

### Post by Espreon on 2007-07-26
I use Beryl SVN and Compiz-Fusion+AWN+Screenlets+Affinity on a Dell Laptop that was designed for Winblows and no overheating here. BTW what Is your video card?

---

### Post by pointone on 2007-07-26
What you could try is disabling Beryl then running another 3D application to try to stress your video card and see if it overheats / crashes. If not, then the problem probably lies elsewhere. I would highly doubt Beryl would be able to stress your card enough to cause overheating, though--not unless you're constantly rotating the cube and whatnot.

---

### Post by Gan Quan on 2007-07-27
> **Espreon said:**
> what Is your video card?
nVidia Quadro NVS 135M.

> **pointone said:**
> What you could try is disabling Beryl then running another 3D application to try to stress your video card and see if it overheats / crashes. If not, then the problem probably lies elsewhere. I would highly doubt Beryl would be able to stress your card enough to cause overheating, though--not unless you're constantly rotating the cube and whatnot.
I tried glxgears, with beryl disabled, it didn't crash but I doubt glxgears can add enough load to my vid card.
I also tried Compiz, it crashes too, just like Beryl.
I even tried Windows, using this free Windows program found [here](http://freestone-group.com/video-card-stability-test.htm) (I know it's better to test a 3d game or something, but all I got on Windows is the Windows XP Home CD came with my laptop), this program runs for more than 2 hours without any problem, it's still running while I'm writing this post. The laptop feels as heated as it was in Beryl, so I'm wondering if it's because linux doesn't handle the video card as good as Windows does (don't flame me, I love linux), I also found that the hard disk is noisier in ubuntu than in Windows, but this is probably because I gave ubuntu 100GB spaces, and /, /usr, /var, /home are in different partitions, while Windows only got 20GB space in a single partition.

btw, this windows program gave me a terrible terrible score, while GeForce 6600 GT got 880, my NVS 135M only got 24!!! Although it is not a "gaming" video card, but I thought it should be enough for desktop use, what the heck? even GeForce4 MX 440SE got 120..

---

### Post by Soybean on 2007-07-27
Beryl definitely can cause video card overheating. I know it doesn't *look* like it's doing all that much, especially when it's just sitting there, but Beryl is actually very hard on the video card. Most 3d apps use the video card to render a bunch of relatively small objects that can be a little blurry -- that's what the card's designed for. Beryl needs to render one huge object, with a bunch of overlapping high-res textures that need to be able to move independent of one another. It's harder than it looks. ;)

I have a Dell laptop that sometimes locks up due to overheating, after about 5 or 6 hours straight of a full 3d game, or after 30 minutes to an hour of Beryl. So yeah... it's a hardware problem... but not likely one they're going to fix, and it'll probably stop bothering you if you drop beryl.

---

