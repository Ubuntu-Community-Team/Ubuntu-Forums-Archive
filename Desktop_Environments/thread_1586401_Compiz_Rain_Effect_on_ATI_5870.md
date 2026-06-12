---
title: "Compiz Rain Effect on ATI 5870"
date: 2010-10-01
forum: Desktop Environments
---

### Post by HeavyWeaponsGuy on 2010-10-01
So... I'm the unfortunate generic ATI user, who happens to own a 5870 for gaming on Windows, but from what I understand right now the Open Source Radeon driver does not support 3D acceleration on Ubuntu right now... so I am forced to use FGLRX. My question is, when I attempt to use the rain effect, my screen dims and most of it becomes black or illegible. No other effect happens... all other effects work ( as far as I can tell ) including fire, but Rain simply will not function as intended.

Is there a way to fix this, or does FGLRX just not like the Rain effect?

---

### Post by sendblink23 on 2010-10-02
Me as well... the whole screen goes dark when activating rain

very weird *CF 5770 10.04 LTS x64 - using FGLRX driver

---

### Post by HeavyWeaponsGuy on 2010-10-02
10.10RC's FGLRX solved the problem. First time I've ever used an RC for Linux, and it works surprisingly just fine.


Solved for 10.10

---

### Post by coffeecat on 2010-10-02
I realise that you've solved your problem by using 10.10, but I thought I would pick this point up. 

> **HeavyWeaponsGuy said:**
> So... I'm the unfortunate generic ATI user, who happens to own a 5870 for gaming on Windows, but from what I understand right now the Open Source Radeon driver does not support 3D acceleration on Ubuntu right now... so I am forced to use FGLRX.

Not quite. I guess it must depend on your particular card. I get 3D acceleration sufficient for my needs with the open source driver and both the Mobility Radeon HD4200 on my laptop and the Radeon HD4350 in the desktop machine I'm posting from now. That's with both Lucid and Maverick. No problem with the rain effect and no problem with any of the compiz effects I've tried so far. In fact I'm very pleased. But I'm not a gamer so I accept that the open source driver might not be up to the demands of gaming.

I think it's fair to say ymmv with ATI. Did you try the open source driver with your 5870?

---

### Post by HeavyWeaponsGuy on 2010-10-02
> **coffeecat said:**
> I realise that you've solved your problem by using 10.10, but I thought I would pick this point up. 



Not quite. I guess it must depend on your particular card. I get 3D acceleration sufficient for my needs with the open source driver and both the Mobility Radeon HD4200 on my laptop and the Radeon HD4350 in the desktop machine I'm posting from now. That's with both Lucid and Maverick. No problem with the rain effect and no problem with any of the compiz effects I've tried so far. In fact I'm very pleased. But I'm not a gamer so I accept that the open source driver might not be up to the demands of gaming.

I think it's fair to say ymmv with ATI. Did you try the open source driver with your 5870?

Currently, open source driver does not support the Evergreen (5x00) series for 3D acceleration.

---

### Post by sendblink23 on 2010-10-02
> **HeavyWeaponsGuy said:**
> 10.10RC's FGLRX solved the problem. First time I've ever used an RC for Linux, and it works surprisingly just fine.


Solved for 10.10

Just installed 10.10... I can confirm the regular FGLRX works perfectly fine with Rain effect ;)

---

