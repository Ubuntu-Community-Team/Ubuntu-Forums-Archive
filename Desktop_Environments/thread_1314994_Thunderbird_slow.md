---
title: "Thunderbird slow"
date: 2009-11-04
forum: Desktop Environments
---

### Post by gstovall on 2009-11-04
About a week ago, on Ubuntu 9.04, Thunderbird suddenly became slow as molasses, and the malaise seemed to spread to other apps when thunderbird was running.  Despite the fact that top did not indicate anything amiss.

I noticed that primary hard drive was starting to show errors, and it had slipped back int udma5 mode, so I decided to replace the hard drive and do a fresh install of Ubuntu 9.10 at the same time.

Brought over .mozilla-thunderbird from my old disk, went through it and removed all the .msf files so the indexes would be rebuilt on the new drive, and started thunderbird up.  Even after waiting for all the indexes to be rebuilt, the problem remains.  When thunderbird is running, the system is slow, and it is VERY slow to change windows between thunderbird and any application.

Been googling, and so far, all I can find is the .msf removal suggestion...starting to wonder if there was some recent Ubuntu update that is playing mokey business.

Thanks if you have any insight!

---

### Post by gstovall on 2009-11-04
Shoot...I didn't give the correct order...I performed an UPGRADE from 9.04 to 9.10 when 9.10 was released, and it was at THAT time that I began having problems...I did not have problems on 9.04.  I began focusing on the hardware issues that I was seeing, so I did not glom onto the fact that it most likely IS a problem between Ubuntu 9.10 and Thunderbird 2.0.0.23...

---

### Post by gstovall on 2009-11-04
One more reply, and hopefully I'll shut up...I don't know whether the root cause is in Ubuntu 9.10 or in Thunderbird 2.0.0.23, but Thunderbird 3.0 beta 4 build 5 is not suffering the slowdowns.

---

### Post by brookie on 2009-11-06
Hi,
I've been using Thunderbird a long time in both WinXP and Intrepid. Unfortunately there is some problem in Karmic. I can confirm that it runs really slow under Karmic. There are at least a couple of bugs reported at Launchpad about this. I suggest to search launchpad for the bug and add your comments so that it may get some attention. 

In the meantime I went back to Evolution in Karmic. It handles my imap gmail account flawlessly including using my google contacts. It also handles reading and writing to my google calendar as well. It did not work both ways in Intrepid, hence, my use of Thunderbird. Also, Evolution in Karmic is as snappy as Thunderbird used to be. 

Cheers, 
Brook

---

### Post by Johnr123 on 2009-11-08
I also have a very slow Thunderbird after upgrading to Karmic. Not only slow, but while reading an email it refreshes the screen and of course take a second or two to do that, totally interrupting the flow of my reading. That's just rude.

I have been thinking of switching to evolution also, but the last time I looked at evolution I couldn't for the life of me figure out how to import emails and folders, etc from Thunderbird. Maybe I'll look at that again. No doubt I missed something.

Cheers,
John

---

### Post by karatedog on 2009-11-23
I also experience slowdowns with Thunderbird after updating to Karmic, my luck is that I only experience it, when sending mail. Thunderbird slows down to a crawl, and an OS warning window appears, that TB is not responding. Then in a few seconds it's back on track again.
During these slowdowns, `top` says TB eats about 4% CPU.

---

### Post by lightstream on 2009-11-25
I had been using Thunderbird up until I upgraded to Karmic, yesterday, at which point it became not only slow and flickery, but would hang completely when I tried to view a particularly full mailbox.

I use IMAP, and some folders contain 10s of thousands of messages.

I've changed to Evolution also, and it doesn't appear to have any such problem.

---

