---
title: "Ubuntu 6.06 won't start up or install"
date: 2006-06-30
forum: Desktop Environments
---

### Post by Vulrath on 2006-06-30
I recently decided to put Ubuntu 6.06 on my desktop, and it won't start up.  Every time I get past the bootup screen, I get a small rectangular box with artifacts in it and a blank brown screen.  The same happens when I try to do anything in ver. 5.10.  What am I doing wrong?  Could Ubuntu not like motherboard (ASUS P5N32-SLI Deluxe)?

---

### Post by swodniW on 2006-07-03
Getting something similar to this, same mobo, boot off the live cd and choose the Install option and then just stops, blank screen with a cursor, like a terminal with the $prompt set to an empty string \\:D/

---

### Post by Vulrath on 2006-07-06
I'm beginning to think all forms of Ubuntu just don't like this board.

---

### Post by dpaint4 on 2006-07-06
Hm! I can't tell you what's happening but I can tell you that the EXACT same symptoms occured on my machine yesterday when I tried to put it to sleep for the first time and then bring it back from sleep.

The 'sleep' thing went very roughly and looked more like a crash to me than anything all too restful. When I opened my laptop back up, it proceed through the very thing you described, and then eventually came out of it and displayed the desktop.

I swore never to try to sleep it again and promptly shut it down.

Anyway, the reason I'm telling you this is because I think you might be closer than you think to actually booting. 

How long have you left it? You should give it a few minutes and see if it comes out of it. That'd be interesting information.

---

### Post by mozz10844 on 2006-07-06
I get the same, I think it's because of my RAM.

---

### Post by Vulrath on 2006-07-06
> 
How long have you left it? You should give it a few minutes and see if it comes out of it. That'd be interesting information.

I left it alone for about a half an hour and it didn't do anything.

Now it won't even give me that.  It'll boot to what looks almost like the server interface for a few seconds then freezes with a blank screen.

---

### Post by Vulrath on 2006-07-07
An update on my problems:

I fixed it by first disabling the DMA and then using the noapic nolapic command on the live CD options menu.
The entirety of my additiions to the boot options line looks like this:
> ide=nodma noapic nolapic

Thanks for your help, everyone.

---

