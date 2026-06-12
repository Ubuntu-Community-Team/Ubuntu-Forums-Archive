---
title: "Clicking noises after installing compiz"
date: 2007-07-31
forum: Desktop Effects &amp; Customization
---

### Post by Mr_Mason on 2007-07-31
Hello,
       
I have just installed compiz on my laptop with 7.04 and i hear clicking noises coming from inside my laptop when using the effects does anyone know what this is and how to fix it?

---

### Post by steveneddy on 2007-07-31
The hard drive?

---

### Post by c3007223 on 2007-07-31
No, I don't think that it is the hard drive as  I think I am having the same problem. I notice that when I have the wobbly windows plugin enabled in compiz fusion, that there is a very faint clicking noise while I am moving windows around the screen- IE when I make windows wobble. That is the only time that I hear the noise. I did not notice this previously with compiz.

For the curious, I have a 2 1/2 year old Dell Inspiron 510m laptop, 1.8 GHz pentium M 64 MB shared video memory, 512 MB system memory. Running Fiesty Fawn.

---

### Post by Mr_Mason on 2007-08-01
No actually i do belive it could be the harddrive as it is coming from the area where the harddrive is loacated.
This cant be good for my laptop.

---

### Post by steveneddy on 2007-08-05
If, for instance, you are running an application that would require lots of memory, more than you have installed lets say, then the HD will go to the swap partition and the sound you hear may be the HD going from swap (the page files) to the application section of the HD. In essence, "thrashing" the HD with the use of Compiz. 

Try upping the memory or turning off some of the features in Compiz to see if that helps.

Another thought, it may be coming from the speakers also.

Something to think about.

---

### Post by levele304 on 2007-08-26
I am experiencing the same problem after a successfull CompizFusion installation on Ubuntu Feisty,

I use a Dell Laptop 6400 with an ATI X1400 vid card.


If the problem is indeed a SWAP that is not big enough, do I resize thru GParted? (I also dual boot with XP)

---

### Post by levele304 on 2007-08-27
Ok , so I successfully resized my SWAP.

The noise is still there but slightly less? (maybe this is just my imagination)

You mentioned a problem with the speakers..  Would installing Compiz cause any changes to the speaker?  

If anyone else has experienced this laptop noise problem after installing CompizFusion, please let me know how you fixed it !

---

### Post by levele304 on 2007-08-27
The noise is closer to a 'chirping' noise rather than a 'ticking' noise.

If that helps at all lol..

Again, my laptop is a Dell 6400 w/ 1GB of RAM and a ATI X1400 vid card.  

Does anyone know of a good hardware diagnostic file that would pick up any irregularities/strains on my laptop?

---

### Post by FuturePilot on 2007-08-27
That could possibly be coming from the graphics card. I have an old GeForce2 Go 32MB and anytime it encounters something graphically intense such as loading Beryl or something like that, I can hear like a squealing noise (chirping?) coming from the computer.

---

### Post by levele304 on 2007-08-27
Do you know if this chirping is unhealthy for the vid card or just a small anoyance?

Any way to check?

---

### Post by FuturePilot on 2007-08-27
I'm pretty sure it's just an annoyance. I've been using Ubuntu on that laptop for over a year now and nothing bad has ever happened to it.

---

### Post by Meyithi on 2007-08-27
Sounds like a "leaky capacitor" on the motherboard, I have a "leaky capacitor" on my desktop graphic card (7900GS) and it whistles whenever it's in use.

It's quite common and usually fine, however if you have a warrantee of some sorts get it fixed just to be safe.

---

### Post by d0gbert on 2007-11-12
I experience the same thing after enabling Compiz in Ubuntu 7.10 on my Dell e1505 (ATI Mobility Radeon X1300) .  When I enable the effects and then open a web page and scroll up and down, I hear a "tick...tick...tick" as the page scrolls up and down. It's pretty quiet but still audible.

---

### Post by nickelby on 2007-11-13
Perhaps you could try

sudo hdparm -B 254 /dev/sda

(assuming /dev/sda is your hard drive) to see if that helps?

---

