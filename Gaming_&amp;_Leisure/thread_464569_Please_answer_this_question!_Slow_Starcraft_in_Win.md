---
title: "Please answer this question! Slow Starcraft in Wine"
date: 2007-06-04
forum: Gaming &amp; Leisure
---

### Post by acorn22 on 2007-06-04
I, like many other people, have decided to re-install Starcraft with the announcment of SCII to get back into the game. Last time I played I was using windows, but now that I am using Ubuntu I have to use wine.

I followed several howto's and got the game itself installed very easily. However it is VERY slow. I used the nice -20 (in 3 different variations) and that helped -hardly though. 

The game is still unplayable and I would like to get this working :/ 

I am using wine 0.9.30
Ubuntu Edgy (actually Mint, but it is havily based on ubuntu)
I don't think my system specs matter because I have heard of people with a gig of ram having this same problem! Just in case: 320MB ram 32MB video card (with nvidia driver) 900Mhz Celeron.

I wonder if just using qeumu would actually be faster? What do you think?

---

### Post by Neo40 on 2007-06-04
Starcraft plays well on my system (Atlhon 1.4Ghz, 750M). I use Cedega instead wine.
And my system is actually MintLinux.
The game is slow if I not use  the command nice (nice -n 16 cedega)

---

### Post by hikaricore on 2007-06-05
You also have about twice the system as the OP.

Cedega does not make the difference and the OP also said they tried nice levels.

I think the OP's video card is just underpowered.

---

### Post by rrenaud on 2007-06-07
I am using wine 0.9.33 with Ubuntu Feisty on a 1800 mhz sempron.  Likewise have very poor starcraft performance under wine.  I think it may be because I am using the vesa video driver.  It's kind of sad that a 6 month old machine won't run a 9 year old game reasonably.

---

### Post by z0phi3l on 2007-06-07
> **rrenaud said:**
> I am using wine 0.9.33 with Ubuntu Feisty on a 1800 mhz sempron.  Likewise have very poor starcraft performance under wine.  I think it may be because I am using the vesa video driver.  It's kind of sad that a 6 month old machine won't run a 9 year old game reasonably.

You need a decent video card :/

---

### Post by rrenaud on 2007-06-07
The system is capable of playing warcraft 3 when it's booted to windows.  I tried playing around with the fglrx drivers, and I even had the war3 demo running okay under ubuntu, but still starcraft wasn't running well.

---

### Post by kamaboko on 2007-06-08
> **acorn22 said:**
> I, like many other people, have decided to re-install Starcraft with the announcment of SCII to get back into the game. Last time I played I was using windows, but now that I am using Ubuntu I have to use wine.

I followed several howto's and got the game itself installed very easily. However it is VERY slow. I used the nice -20 (in 3 different variations) and that helped -hardly though. 

The game is still unplayable and I would like to get this working :/ 

I am using wine 0.9.30
Ubuntu Edgy (actually Mint, but it is havily based on ubuntu)
I don't think my system specs matter because I have heard of people with a gig of ram having this same problem! Just in case: 320MB ram 32MB video card (with nvidia driver) 900Mhz Celeron.

I wonder if just using qeumu would actually be faster? What do you think?

Here's a thought.  Why not play it on the OS your CD was intended for?

---

### Post by acorn22 on 2007-06-08
> **kamaboko said:**
> Here's a thought.  Why not play it on the OS your CD was intended for?

I don't even feel like answering that.

---

### Post by hikaricore on 2007-06-08
> **kamaboko said:**
> Here's a thought.  Why not play it on the OS your CD was intended for?

That was uncalled for.  GTFO.

---

### Post by Dritzen on 2007-06-08
My system is decent and even I had trouble running Starcraft at a proper speed.

I ran winecfg and went to the audio tab at the top, then changed "Hardware Acceleration" from Full to Emulation

The next time I ran the game, it ran smoothly.

---

### Post by acorn22 on 2007-06-08
lmao Kamboko is a troll. [http://ubuntuforums.org/search.php?searchid=21721688](http://ubuntuforums.org/search.php?searchid=21721688)

Dritzen, I will try that.

---

### Post by Enverex on 2007-06-08
Wine changed some big things that slowed apps like Starcraft down massively between version 0.9.15 and 0.9.16.

So you have a few options. You could:

Try adding the registry key "DirectDrawRenderer" with the value "opengl" to HKCU > Software > Wine > Direct3D.
Use Wine 0.9.15.
Upgrade your hardware (because of this it needs more CPU power so people with a fast CPU wont notice the slowdown).

Hopefully the first suggestion should fix it for you. Although I'd make sure you have OpenGL hardware accelleration in Linux ("glxinfo | grep -i direct" should say Yes).

The VESA driver will never give good performance with anything.

---

### Post by Wulfrunner on 2009-03-16
I remember using an old version of wine with Redhat 6.0 on a Pentium 133Mhz and a Vesa video card and it ran Starcraft flawlessly. 

I have a huge issue with wine failing to run Starcraft in a playable manner on my Athlon 1600 / Radeon 9600. Running Starcraft on my Core2Duo E4500 / ATI Radeon 2400Pro takes 100% CPU power -- World of Warcraft takes maybe 30-40%.

---

