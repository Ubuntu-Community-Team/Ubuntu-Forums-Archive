---
title: "WoW running slow with poor graphics using Wine"
date: 2007-01-10
forum: Gaming &amp; Leisure
---

### Post by MsTiggy on 2007-01-10
I recently installed WoW using Wine, and I'm having some problems. The graphics look like crap (all the characters/creatures are see-through and dark, landscapes sometimes don't render at all), and about 50% of the time, the frame rate is ridiculously slow (10-15 fps, if not less). I tried turning down the video settings to see if that would help the frame rate, but it didn't. Now, I had the same frame rate problem when I ran it in windows, but the graphics problem is new to Ubuntu.

I'm not completely computer illiterate, but I am new to Ubuntu (and fairly new to Unix/Linux in general), so step-by-step instructions would really be helpful, if possible.

Thanks in advance!

EDIT:  I did "tweak #1 from this howto: [https://help.ubuntu.com/community/WorldofWarcraft](https://help.ubuntu.com/community/WorldofWarcraft) and it fixed the graphics!  Not sure if the fps problem is fixed yet, though, I'll have to play some more and find out.

---

### Post by Lord Illidan on 2007-01-10
> **MsTiggy said:**
> I recently installed WoW using Wine, and I'm having some problems. The graphics look like crap (all the characters/creatures are see-through and dark, landscapes sometimes don't render at all), and about 50% of the time, the frame rate is ridiculously slow (10-15 fps, if not less). I tried turning down the video settings to see if that would help the frame rate, but it didn't. Now, I had the same frame rate problem when I ran it in windows, but the graphics problem is new to Ubuntu.

I'm not completely computer illiterate, but I am new to Ubuntu (and fairly new to Unix/Linux in general), so step-by-step instructions would really be helpful, if possible.

Thanks in advance!

What make of graphics card have you got?

---

### Post by MsTiggy on 2007-01-10
... How would I go about finding that out?  Like I said, really new to Ubuntu...

---

### Post by meng on 2007-01-10
> **MsTiggy said:**
> ... How would I go about finding that out?  Like I said, really new to Ubuntu...
Well the video card is part of your hardware, it has nothing to do with Ubuntu per se. If you don't know what hardware you've got, then try this at the command line:
lspci
this should list a bunch of devices including your graphics card.

And posting the same problem in two different threads 1. won't help you get your problem solved any quicker 2. is frowned upon.

---

### Post by MsTiggy on 2007-01-10
Yeah, I know posting it in two different threads was a bad idea, I wanted to delete the other one, as I figured this would be a better thread, but I couldn't figure out how.

Anyway, this is what lspci told me:

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R250 Lf [FireGL 9000] (rev 02)

---

### Post by meng on 2007-01-10
Okay, you've got an ATI video card. (Congratulations) If you want better 3d performance (trust me, you do) then you need to install the proprietary drivers. Follow this guide closely:
[http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)

---

### Post by MsTiggy on 2007-01-10
Ok, so I followed the guide to the letter (as far as I know).  But now, whenever I try to get onto the server, everything freezes.  I can't even alt-tab out of the program.  My whole computer freezes, and I have to force a restart.

When I run $ sudo apt-get update

it goes through everything, and then at the end it spits out

W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: You may want to run apt-get update to correct these problems

Would that have something to do with it?

---

### Post by meng on 2007-01-10
The GPG key error is not a problem. Ordinarily, there is key authentication with the repository to ensure that you are downloading from a bona fide source. You can override the lack of verification if/when you need to download an updated wine package from budgetdedicated.

---

### Post by meng on 2007-01-10
Correction, it now seems there is a solution (hasn't been until recently though):
[http://www.ubuntuforums.org/showthread.php?t=335324](http://www.ubuntuforums.org/showthread.php?t=335324)

---

