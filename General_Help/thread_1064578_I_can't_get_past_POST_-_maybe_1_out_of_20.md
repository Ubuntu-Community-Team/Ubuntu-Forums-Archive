---
title: "I can't get past POST - maybe 1 out of 20??"
date: 2009-02-09
forum: General Help
---

### Post by PsychedelicWonders on 2009-02-09
I've had a serious issue with getting past POST lately and I don't understand why. 

There was never an issue before, the computer was not moved. 

The ONLY thing That changed recently was that I added I 2nd monitor.

I was told somethng wasn't seated right. So I took it apart and removed and reconncted most of the computer. 

Twice. 

How can I find out what the real issue is?

---

### Post by hwttdz on 2009-02-09
Sounds similar to a problem I have.  Except for me it works 3 times out of 4.  I've found that when I plug in my floppy/cardreader drive it doesn't boot all the time.  I believe this is caused by the increased power draw, but I'm not entirely sure.  The fix (and test) would be either to increase your power available or decrease your power consumption.  For me, I'm not using all my hard disks, so I figure if I unplug a couple I should be good to go.  This seems especially likely as a monitor is a huge power hog.

---

### Post by PsychedelicWonders on 2009-02-09
hmm.

But my monitors have their own power cord?

So how can that affect the HTPC?

This is the power supply I have, I had researched doing this many monitors (I actually plan on adding a 3rd monitor and a 46" lcd tv to the mix also) but this one should be enough no?...

[http://www.newegg.com/Product/Product.aspx?Item=N82E16817182149](http://www.newegg.com/Product/Product.aspx?Item=N82E16817182149)

What do you guys think?

should be enough right?

---

### Post by PsychedelicWonders on 2009-02-20
Now everything loads up fine...

And I didnt change anything

So how can I find out what the problem was of not being able to get past POST?

---

### Post by Therion on 2009-02-20
Intermittent problems like this are the hardest to solve.  If your system is not passing POST, are you getting any POST-code error-beeps?  That would be step one.  The usual suspects are (in order of frequency from my experience) RAM modules either needing to be re-seated or going bad, some other card (PCI, PCI-e, whatever) needing a re-seat, a crappy cable that's finally decided to give up the ghost or, more specifically, one of those older SATA cables that don't have clips that has worked itself loose and needs a re-seating.

If the problem persists after re-seating cards and memory and double checking cables and cable-connections, I'd swap out the RAM modules with a "known good" module or pair and work my way out from there.

---

### Post by jerome1232 on 2009-02-20
When I see "intermittent" I immediately suspect the power supply first. As they age psu's tend to produce less power over time. 

To figure this one out your going to have to play the "swap everything out one at a time game" to figure out which component is causing the issue, which is even more difficult to figure out when the problem is no longer there!

---

### Post by Yellow Pasque on 2009-02-20
Unless you're running a power-hungry system with multiple video cards, that PSU is capable of delivering WAY more power than you'll ever need.

If you don't have spare RAM, I suggest running memtest, found in the GRUB/boot menu (and even if you do, running memtest is always a good idea to verify your RAM's integrity).

---

