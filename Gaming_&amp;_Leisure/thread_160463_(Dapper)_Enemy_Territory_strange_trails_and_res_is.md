---
title: "(Dapper) Enemy Territory: strange trails and res issues"
date: 2006-04-15
forum: Gaming &amp; Leisure
---

### Post by beefsprocket on 2006-04-15
There was an xorg update of some sort 2 days ago that has done something not nice to Enemy Territory. Specifically, running at anything other than 1024x768 results in first, the game taking up only the left and bottom 3/4 of the screen, and second, so really terrible beige sort of ghosting effect. 

I used to run it at 1280x1024 without any problems, taking up the full screen. I've tried various other games (ut2004 for one) and the same res issue applies whereas it didn't before. 

Anyone know what happened in xorg to cause this? Any suggestions short of finding all the needed .debs and downgrading?

---

### Post by Perfect Storm on 2006-04-15
Dapper is still in development so these things happen and that's why Dapper shouldn't be used as main OS atm. The best thing to do is to report the bug and hope they fixed xorg quickly.

---

### Post by Schizofrenia on 2006-04-20
Hi!
Ehi beefsprocket... What do you mean for "ghosting effect"?
Do you mean that while playing ET (or TCE in my case...) you see the frames of the game and the system has some problems about correct rendering of the frames?
I think that I have the same problem... I have also done that xorg upgrade.... :???: :???: :-k :???: 

What do you think about a downgrade? Is it possible?

P.S Sorry for my English, I'm Italian... :roll: :D :mrgreen:

---

### Post by beefsprocket on 2006-04-22
Yeah, I notice it especially when there are large explosions like artillery or airstrikes. Things stay rendered on the screen when they should be replaced by whatever should be there. Sort of like extreme ghosting that fills your whole screen, or when you move a window over (on your desktop) another and it draws itself over top even after the window is gone.

Not sure about the downgrade -- I looked in my /var/cache/apt/archives, tried a few of the older xserver and relted packages, but no good. I'm wondering if it is the new NVIDIA driver.

---

### Post by Schizofrenia on 2006-04-22
Yeah!! I solved my problem!! No more "ghosting effects" and bad renderings... eh eh!!
I noticed that in the "Option menu ----> System" of games such like ET or TCE there's an option that said "Sync every frame"... If you play with that option enabled you'll have no frame rendering problems... :mrgreen: 

About Nvidia Drivers.... They're still working very fine on my machine, I don't think they could be the main problem... :-k 

Thx! Bye!

---

