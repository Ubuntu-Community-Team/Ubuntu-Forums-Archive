---
title: "Ati + Xgl + Gnome"
date: 2007-09-17
forum: Desktop Environments
---

### Post by Criminosis on 2007-09-17
I'm sure that title is a common sight for all. And brings sores to many. But I think i am close to having my set up working (and i know it is possible with the numerous Youtube videos, so i figured it was time to bite the bullet and install (or attempt rather) Compiz on my desktop (with an ATI card) after having success with my Nvidia Laptop (yes i know Nvidia is loads easier :-k). 

Anyways some time, I've gotten 

```
direct rendering: Yes
```

and

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series
OpenGL version string: 2.0.6747 (8.40.4)

```

So I am guessing that I am close.  However, following per guide's instructions, I constructed a Gnome with XGL session. Logged into that and everything is just awful. Bars and menus are "scratched" out (almost what i would call the visual image of sound static). I'm rather lost on where to go from here as no guide I can locate troubleshoots from this point, and am begging to dread unsupportation. My purpose for those wondering why push on is of course for Compiz Fusion. 

This is the guide I followed to this point [http://ubuntuforums.org/showthread.php?t=488385](http://ubuntuforums.org/showthread.php?t=488385)

Help would be grand.:guitar:

---

### Post by Criminosis on 2007-09-18
bump

---

### Post by mtbsoft on 2007-09-18
Sadly, all I can add is "been there, done that"... gone back to Beryl.  I tried four times to get Compiz working on my ATI x1400 and got no closer than you have so went back to Beryl which is simple by comparison.

---

### Post by Criminosis on 2007-09-18
That's grand for you, but I've seen it done. I know it can be done, I just need someone who has had this experience and surpassed it. If it really and truely is impossible, well i've got my laptop for show floors i suppose, but having my X1600 graphic card instead of my Nividia Integrated, would be very benifical.

---

### Post by Romanus81 on 2007-09-18
Are you running fglrx?
I used the same guide to get compiz working, what I did was install fglrx, 
try typing 
```
fglrxinfo
```
you should get something like
> display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X300/X550/X1050 Series
OpenGL version string: 2.0.6334 **(8.34.8 )**
The bold numbers are the version number. If you don't have FGLRX installed, then look at this

[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194) 
^This is the guide I followed, just make sure that when you install fglrx, that it is version 8.34.8, I know they released a version after that, which broke everything, then a version that fixed it for a series of cards with a certain chipset, and next month they are working on one that SHOULD fix it for all cards. 8.34.8 is the version that ships with ubuntu.
I haven't tried the last (fixed) driver, so you might look at it and see if you can risk it.
EDIT: And don't worry if Direct Rendering: No shows up, it will still work.

---

### Post by Criminosis on 2007-09-19
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1600 Series
OpenGL version string: 2.0.6747 (8.40.4)

```

Guessing I'm running the busted one? lol

---

### Post by Criminosis on 2007-09-19
Bump for hope

---

### Post by swisscow on 2007-09-20
If you have run fglrxinfo and got those results you mentioned, then you have fglrx working fine. You must then, for compiz/beryl/compiz fusion, install **xgl and compiz/bery/compiz fusion **following whatever guide you can find - there are loads out there but take note of which you use incase it all goes wrong.

FYI I believe that ATI will be releasing (or may have done so already) a driver for their gfx cards which may negate the need for XGL and support AIGLX instead. Perhaps someone out there knows more?

---

### Post by Romanus81 on 2007-09-21
Well, if I were you I'd find a way to backup my system, because I had this problem, and to solve it I had to reinstall ubuntu from scratch and follow the guides exactly, but if you have had ubuntu for awhile, I can see that might be a problem.

Before you do things it would be a good idea to look for a way to backup your system, you might try upgrading to the most recent fglrx driver, 8.41.7, or you might ask around the "Desktop Effects and Customization" to see if anyone knows how to switch back to the fglrx version that shipped with ubuntu. 

[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087) 
Try backing up Ubuntu, and placing the somewhere other than your ubuntu partition, if you break it tying to fix anything, you can make an easy clean install and restore.

---

