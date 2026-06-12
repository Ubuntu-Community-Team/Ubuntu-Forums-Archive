---
title: "Gnomad question"
date: 2006-01-26
forum: Desktop Environments
---

### Post by painreliever on 2006-01-26
Hey, just a quick one (with a quick answer I hope!)

I've installed Gnomad and it runs fine as long as I launch it from Terminal as root, as for some reason I don't have the right permissions for hotplug as user. But that's not the real problem - if anyone does know how to sort this, please tell me, but otherwise my problem is thus:

When I try and connect my player (I'm using a Zen Touch), Gnomad crashes and I get the following message in the Terminal window:

gnomad2: symbol lookup error: gnomad2: undefined symbol: NJB_Set_Turbo_Mode

Even if I got into preferences and disable Turbo Mode BEFORE I connect my Zen, it STILL crashes. I've tried googling it to no avail.

Any ideas?

Ta

---

### Post by Lord Illidan on 2006-01-26
You installed Gnomad 2 from synaptic?

Cos my media player, Creative Zen Micro works excellently with it.. and no need for root/sudo..

Did you install libnjb0, and all the required dependencies?

---

### Post by painreliever on 2006-01-26
Yep, installed it from Synaptic. 

Just had a quick look in Synaptic, and it says i have libnjb5, not libnjb0. Could this be why?

---

### Post by Lord Illidan on 2006-01-26
No, sorry that was a mistake.. libnjb5 is what it needs...

Have you tried neutrino?

---

### Post by painreliever on 2006-01-26
Neutrino just crashes. Stops responding ...

Really don't get this.

---

### Post by Anti-Establishment on 2006-01-30
Can anyone explain this to me, when I scan in Gnomad for my jukebox I get the following messages

> Could not open jukebox:
njb3_read_codecs: short read on USB data pipe

> No jukeboxes found on USB bus 

And a few others like that

I can't for the life of me figure how to put songs on my Zen Micro and other threads I have looked at offer little or no help to a complete and utter newbie. Why isn't Gnomad picking up the Zen?

---

### Post by PeteVenkman on 2006-02-06
I'm having the same problem with a 1st gen Zen.

gnomad2: symbol lookup error: gnomad2: undefined symbol: NJB_Set_Turbo_Mode

I'm on 5.10 Breezy.  I actually manually compiled and installed the latest version of gnomad2 and got this error so I uninstalled and installed it clean from synaptic.  Same thing.


As for neutrino, I've had the same experience with it.  It runs great sometimes and then BANG... it will freeze completely.

---

