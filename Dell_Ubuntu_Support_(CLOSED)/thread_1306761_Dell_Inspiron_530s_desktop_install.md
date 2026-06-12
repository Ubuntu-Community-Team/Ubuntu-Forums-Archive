---
title: "Dell Inspiron 530s desktop install"
date: 2009-10-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by peterm3 on 2009-10-30
I am being driven mad trying to install 9.10 or indeed 8.10 ubuntu. I can't even run the live mode. I have tried changing the IDE mode to RAID, but that doesn't help. It just stops on the black and white Ubuntu logo.
I have a Core2Duo, E8400 @ 3 GHz.
I have tried Ubuntu before on a Toshiba laptop, and it did seem to work OK for a n00b who can only use a GUI. Seems very frustrating how hard in 2009 it can be to install and operating system! What is the secret, I ahve googled and found no solution, apart from the IDE to RIAD, which doesn't work for me!
Peter

---

### Post by gbrainin on 2009-10-30
Is it possible that you have a bad burn on your CD?  If not, I've only seen the behaviour you experience on my 530 from the IDE/RAID problem.  You could try the alternate solution of adding all_generic_ide to the boot line.

---

### Post by teward on 2009-10-30
Is it possible that his computer's hardware is incompatible?

---

### Post by peterm3 on 2009-10-31
I have redownloaded and burnt the CD. It is strange as I can't get my Toshiba laptop to boot with 9.10 either. I am totally amazed no-one else is having difficulties. Dell are so common, and they even sell computers with Ubuntu already installed!

---

### Post by Dutchmaster on 2009-10-31
It's not an exact fit, but this might provide some comparison data. My Dell Inspiron 530n desktop (Intel  Dual Core E2180 2.0 Gh w/ 2gb ram) installed without issue. Ethernet recognised. Boot-up fast. Video and sound good. Compiz works great.

---

### Post by teward on 2009-10-31
> **peterm3 said:**
> I have redownloaded and burnt the CD. It is strange as I can't get my Toshiba laptop to boot with 9.10 either. I am totally amazed no-one else is having difficulties. Dell are so common, and they even sell computers with Ubuntu already installed!

They come installed with 8.04, and not 9.* if you have Dell install it.

---

### Post by gbrainin on 2009-10-31
I have successfully run vanilla 8.10 and 9.04 on mine.  Haven't tried 9.10 yet.  Will do so and report back.

---

### Post by gbrainin on 2009-10-31
Running off the 9.10 disc worked just fine.  But I noticed in your original message you noted that you are stuck on the _black and white_ Ubuntu logo.  To the best of my memory, versions earlier than 9.10 used only a color logo.  Are you sure your 8.10 disc is actually 8.10?  If not, I'd try an earlier version to see if that helps at all.

---

### Post by stapel on 2009-10-31
Im have tried to do a clean install of 9.10 64 bit on mine, and i have the same problem. I was running 9.04 32 bit and upgraded from there to 9.10 without problems. Even the 9.10 64 bit live cd works for me. Would really like a solution to this.

---

### Post by peterm3 on 2009-11-01
> **gbrainin said:**
> Running off the 9.10 disc worked just fine.  But I noticed in your original message you noted that you are stuck on the _black and white_ Ubuntu logo.  To the best of my memory, versions earlier than 9.10 used only a color logo.  Are you sure your 8.10 disc is actually 8.10?  If not, I'd try an earlier version to see if that helps at all.

There is a black and white logo to start with. When its working properly, it probably flashes past so quick you don't see it!
I have it running now, by installing onto a USB flash drive. It took me half of the night to get the wireless working using ndiswrapper :(. Ubuntu 9.10 is great once you get it working. But I think Google will have a heck of a job trying to build an easy to install Linux-based OS unless they can radically improve the install experience. Maybe I was just unlucky with two failed CDRs (different brands burnt on two difference machines) or maybe my CD drive doesn't work when booting!
Peter

---

### Post by gbrainin on 2009-11-01
> **peterm3 said:**
> There is a black and white logo to start with. When its working properly, it probably flashes past so quick you don't see it!
I have it running now, by installing onto a USB flash drive. It took me half of the night to get the wireless working using ndiswrapper :(. Ubuntu 9.10 is great once you get it working. But I think Google will have a heck of a job trying to build an easy to install Linux-based OS unless they can radically improve the install experience. Maybe I was just unlucky with two failed CDRs (different brands burnt on two difference machines) or maybe my CD drive doesn't work when booting!
Peter

Well, I'm glad to hear you figured out a way to make it work.  And yeah, ndiswrapper can be a little tricky.

However, the facts that: a) you did get 9.10 to work, and b) other people with 530s can run 9.10 off the CD without issue tells me that you must have some very unusual problem, perhaps with the CD itself or the drive or . . . not sure what.  In any case, glad to hear you worked around it.

---

### Post by Kobus Conradie on 2009-11-15
I'm new to Ubuntu/Linux, mostly a user, although I try and understand how Linux works. Had 9.04 Jaunty Jackelope on my D630 and decided to do the on-line upgrade to 9.10. Now I find that I have to 'start' the laptop a few times to actually get it to boot up. I get the Linux logo that eventually disappears, but there is no HDD activity. I then force shutdown the laptopo with the power button, leave it a few seconds and then try again. My last start-up took 7 attempts. Any ideas?
Thanks

---

