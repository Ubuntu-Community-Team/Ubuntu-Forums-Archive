---
title: "Stop compiz from running checks at startup"
date: 2008-03-05
forum: Desktop Effects &amp; Customization
---

### Post by larryfroot on 2008-03-05
Hi,
I have just got an oldish laptop running with compiz (on a gutsy install) after a struggle with a radeon 9000 card - using the open source driver and hacking xorg.conf did the trick and thank God for these forums! 

In order to run compiz, I need to get it to stop running through its checks that it makes before it starts in the normal sense of the word, so typing SKIP_CHECKS=yes compiz  in a terminal window gets compiz up and running. I have placed that function onto a launcher, but how do I get compiz to stop checks on startup? I have tried editing the session, but that only spat out an error message. 

Thanks for your help. Its been a rocky road with that b****y  radeon and it would be so nice to put the cherry on top of the cake.

PS And if anyone knows how to get compiz to run its funky stuff without me having to reduce the colour depth from 24 to 16 in xorg.conf, I will be very happy to hear from you!

---

### Post by notwen on 2008-03-05
Stickied at the top of the Desktop Effects and Customization thread you will find [this thread]("http://ubuntuforums.org/showthread.php?t=582112").  =p

Please note that you are doing this at your own risk, running Compiz-Fusion w/ blacklisted hardware may have un-expected effects, etc.  I do this w/ my Inspiron 1420n laptop, since my Intel X3100 chipset is also blacklisted.  Hope this is what you're looking for.  =]

---

### Post by kevinatkins on 2008-03-05
Hi,

Go into the hidden .config folder in your home folder, then either create (if it doesn't already exist) or go into the compiz folder in there. Then create a file called 'compiz-manager' into which you need to enter the following:

SKIP_CHECKS=yes

And that's it!

---

### Post by larryfroot on 2008-03-05
Thank you very much, both of you!

---

