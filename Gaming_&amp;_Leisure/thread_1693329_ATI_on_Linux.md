---
title: "ATI on Linux"
date: 2011-02-22
forum: Gaming &amp; Leisure
---

### Post by AdlerMF on 2011-02-22
I'm not sure if this is the right place to ask, but it's mainly for gaming so I posted it here:
I'm about to buy a laptop and I'm considering if I should buy one with an ATI GPU. I used ATI on Linux in early 2009 and I have terrible memories of it... has it improved in the last couple of years?

ATI's 3D acceleration works with Wine's DirectX now?
Also, I'll be using KDE 4, is there currently any known issues with KDE and ATI?

Thanks in advance.

---

### Post by R33D3M33R on 2011-02-23
Wine games, other games and KDE work for me, but there is no doubt that most of the people on this forums will say: "Don't buy ATi" (Even if they last used ATi cards years ago ](*,)).

---

### Post by Perfect Storm on 2011-02-23
> **R33D3M33R said:**
> Wine games, other games and KDE work for me, but there is no doubt that most of the people on this forums will say: "Don't buy ATi" (Even if they last used ATi cards years ago ](*,)).

They are still right - if you look for best performance and features and less headache :popcorn:

---

### Post by mastablasta on 2011-02-23
no problems here with ATI. i think 4000 and 5000 series are ok. 6000 have new drivers, so they might still have some issues.

---

### Post by JDShu on 2011-02-23
For gaming, Nvidia cards are still the best. Older ATI cards will run lower end games, maybe even better than Nvidia in some situations, but they will not run newer games well, if at all. If all you plan to play are low spec games (Braid and Urban Terror work wonderfully on my HD4550) then ATI is great. But for upcoming games (eg. Oilrush) you may want to get an Nvidia card.

---

### Post by mnerobi15 on 2011-02-23
I cant find Linux support for an ATI 550 series tv tuner card. I got the  card for free and was hoping to use it with MythTV but there is no  Linux support on ATI's site for dedicated tuner cards.

---

### Post by R33D3M33R on 2011-02-23
@Performance: this are my test's with HD4670 and Karmic Koala: [PDF]("http://andrej.mernik.eu/racunalo/windows_7_vs_ubuntu_9_10/rezultati/windows_7_vs_ubuntu_9_10.pdf")

---

### Post by mastablasta on 2011-02-23
> **mnerobi15 said:**
> I cant find Linux support for an ATI 550 series tv tuner card. I got the card for free and was hoping to use it with MythTV but there is no Linux support on ATI's site for dedicated tuner cards.
 
TV tunners are a whole different story. as i know only a few are fully supported. Check the mythTV wiki to find out which.

---

### Post by handy on 2011-02-23
This is worth a look for the technically minded patient person:

[http://www.x.org/wiki/RadeonFeature](http://www.x.org/wiki/RadeonFeature)

There is also other info' worth looking at, but those who find the above link stimulating should find them with ease. :)

---

### Post by AdlerMF on 2011-02-23
> **JDShu said:**
> For gaming, Nvidia cards are still the best. Older ATI cards will run lower end games, maybe even better than Nvidia in some situations, but they will not run newer games well, if at all. If all you plan to play are low spec games (Braid and Urban Terror work wonderfully on my HD4550) then ATI is great. But for upcoming games (eg. Oilrush) you may want to get an Nvidia card.
It's only for light games, like Starcraft II. Most if not all of the games I wish to play run on an Intel GMA HD, even if it's on low settings.

Thank you for your answers. It seems that ATI isn't so much of a headache nowadays.

---

### Post by cascade9 on 2011-02-23
With laptops, nVidia sucks now. Too many optimus models, no nvidia linux support for optimus, and manufacturers who dont list that the laptops are optimus in the spec page.

---

### Post by Nutbun on 2011-02-24
I have had both and opted for the ATI card, because it produces nice sharp graphics where the Nvidia graphics always looked a little smudged to me.

---

### Post by brencameron on 2011-02-27
This is my own experience: I am using an ATI Radeon HD 3200 card, and installed the nonfree driver. I'm having no problems whatsoever, but I use Linux Mint 9, so your mileage on Ubuntu might be slightly different. Mint 9 is equivalent to 10.04. I've been able to play several MMO games using Crossover Games, and 7 FPS games from the repos. Nothing has given me issues so far, and my card certainly isn't a high end one.

---

### Post by rajeev1204 on 2011-02-28
> **AdlerMF said:**
> I'm not sure if this is the right place to ask, but it's mainly for gaming so I posted it here:
I'm about to buy a laptop and I'm considering if I should buy one with an ATI GPU. I used ATI on Linux in early 2009 and I have terrible memories of it... has it improved in the last couple of years?

ATI's 3D acceleration works with Wine's DirectX now?
Also, I'll be using KDE 4, is there currently any known issues with KDE and ATI?

Thanks in advance.

ATI and the proprietary drivers have vastly improved over the last year.If you play native linux games like quake wars etc you will not face any issues whatsoever.Catalyst 11.2 also added tear free video and some other laptop features like powerxpress (still experimental though)

Wine performance is not that good since the wine team is supposedly using hacks specifically meant for nvidia cards.Iam not sure about the current status though.

No idea about KDE and ATI,but i dont see why that would be an issue.

Only thing lacking is gpu acceleration of HD videos/ flash etc but frankly its more a linux mess and both nvidia /ATI struggle with it.

Nvidia's VDPAU framework is better at it though and using  vlc and mplayer you can get good gpu acceleration with nvidia cards.

Flash is a different story and adobe themselves dont support any gpu accel in linux due to a lack of a proper standardised video API.

---

