---
title: "Dual Display (1 Laptop, 1 TV) w/ Separate X Screens [ATI x1400 video card]"
date: 2009-03-11
forum: Desktop Environments
---

### Post by Infuego_99 on 2009-03-11
After searching for several days for an answer, I am hoping that someone can help me. Here is my scenario:

Fresh install of Ubuntu 8.10 on Dell laptop
ATI Radeon Mobility X1400 video card
TV connected by S-Video from laptop

I would like to have dual displays (Laptop & TV) with separate X displays so I could have a movie or whatever playing on the TV and still be able to work with multiple desktops on the laptop screen. If possible, I would like to also be able to use Compiz Fusion.

I am definitely a newbie to Ubuntu, so as much detail as possible would be great. I am hoping that I don't have to switch back to Windows to be able to do this(GRRR!!!). I never want to switch back if at all possible. Thanks in advance for everyone's help with this.

---

### Post by FaizanKazi on 2010-04-04
> **Infuego_99 said:**
> After searching for several days for an answer, I am hoping that someone can help me. Here is my scenario:

Fresh install of Ubuntu 8.10 on Dell laptop
ATI Radeon Mobility X1400 video card
TV connected by S-Video from laptop

I would like to have dual displays (Laptop & TV) with separate X displays so I could have a movie or whatever playing on the TV and still be able to work with multiple desktops on the laptop screen. If possible, I would like to also be able to use Compiz Fusion.

I am definitely a newbie to Ubuntu, so as much detail as possible would be great. I am hoping that I don't have to switch back to Windows to be able to do this(GRRR!!!). I never want to switch back if at all possible. Thanks in advance for everyone's help with this.

Hey! wow.. this is old. I have the same problem. Its called a Dual headed display - showing data across two screens. sounds kinda wicked like we're dealing with a mythical creature, and it kinda is. ATI is not very supportive and its not as popular either in the open source community, as opposed to nvidia. So basically they stopped supporting cards like the x1400 in linux.

so we have to resort to the generic drivers which dont use hardware acceleration :( and also dont support dual headed displays i believe :(

unless youre still using ubuntu 8.10 in which case you can load the ATI Proprietary drivers, also called the binary drivers.

---

### Post by FaizanKazi on 2010-04-04
WOAH WOAH WOAH!!! turns out in Ubuntu 10.4 Beta (and maybe even 9.10) you can use the regular drivers (non proprietary/ non Ati) to enable two displays without ANY hiccups!

So i went to System >> Preferences >> Monitors
and then i plugged in my tv on Svideo, turned the tv on, and told it to detect monitors and it DID!!! :)
First the picture was kinda weird, then i set it to a 1024*768 resolution and the picture is so so clear :)

---

