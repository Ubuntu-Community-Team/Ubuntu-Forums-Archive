---
title: "Free space disappearing from root until reboot"
date: 2009-01-03
forum: General Help
---

### Post by allanmills on 2009-01-03
Hello.  My second post here.  New to Ubuntu; have been using it for about 4 weeks and love it.

**_Issue:_**  I have Ubuntu on an ext3 partition of about 6 gigs, of which about 1.7 gigs is free under current setup when I first boot.  I have a swap of about 2 gigs.  

Lately (meaning it didn't always do this) whenever I have my laptop up for several hours, at some point all of my free space is gone, taken up by something unknown to me.  It's usually when I leave it running (which is rare since I'm a truck driver and there aren't many times I leave it up very long unless I'm broken down, as has been the case recently when I noticed this behavior), come back after 1, 2 or more hours and suddenly there's no free space.

Rebooting restores the status quo (of about 1.7 gigs).

I dual-boot Windows XP, so most of my data is on other shared drives.

Environment when this occurs:  I typically am running Opera (for browsing, mail, etc.), Open Office, Dolphin file manager, Amarok for music, and maybe a couple of other things.  Nothing new that I have installed that is running that wasn't running before this started.

Could it be that some kind of verbose logging is taking up all that space?  If so, how to track down what's doing it?  

I've done searches here and on google for similar problems, but haven't found anything similar, perhaps because I was using the wrong search terms.

Even since booting up this time, over less than half an hour, I've watched my free space go from 1.7, to 1.6, and now 1.5 gigs.  

Suggestions?  Thanks for any help!

Allan

---

### Post by ollesbrorsa on 2009-01-03
Hello,

I had a similar problem a while ago. This helped me with that particular issue: [http://ubuntuforums.org/showpost.php?p=6200061&postcount=8](http://ubuntuforums.org/showpost.php?p=6200061&postcount=8)

Br,
ollesbrorsa

---

### Post by allanmills on 2009-01-03
Wow!  I could not believe how quickly your response came, and the link you provided did help.  

What I did (perhaps unadvisedly) was to add "pre-release" sources and I downloaded a kernel which supposedly fixes the bug referenced in the link related to Intel wireless utilization.

I think that fixed the problem (not that I understand much of what it actaully was even after reading the bug reports).

I do, however, have a follow-up query, which would perhaps be better put as a new thread, I'm not sure:

When exploring some of the logs, which are new to me with Ubuntu, I notice that the X.org log (as viewed in KSystemLog) repeats an entry approximately every 10 seconds, as follows:

	Information	intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
	Information	intel(0): I2C device "LVDSDDC_C:ddc2" removed.
	Information	intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
	Information	intel(0): I2C device "LVDSDDC_C:ddc2" removed.
	Information	intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
	Information	intel(0): I2C device "LVDSDDC_C:ddc2" removed.


Can you (or someone else) tell me what this means, and if it is perhaps related to the bug referenced in the link in the reply above?

Thanks again for the quick and helpful response before!  If I can figure out how, I'll add a thank you to your profile.

Allan

---

### Post by ollesbrorsa on 2009-01-05
Hello,

Glad I could be of assistance :)

I'm afraid I can't help you much on the follow up question. I did a search on "LVDSDDC_C:ddc2" and got a whole bunch of hits. For example: [https://bugs.launchpad.net/ubuntu/+bug/292788](https://bugs.launchpad.net/ubuntu/+bug/292788)

This does not mean it is the same that you are experiencing but it might be a place to start digging.

Br,
ollesbrorsa

---

### Post by venomcom on 2009-01-07
Hi,

  I have same problem here, continously getting these messages in Xorg.0.log, and restarting X spuriously:

Information intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
 Information intel(0): I2C device "LVDSDDC_C:ddc2" removed.
 Information intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
 Information intel(0): I2C device "LVDSDDC_C:ddc2" removed.
 Information intel(0): I2C device "LVDSDDC_C:ddc2" registered at address 0xA0.
 Information intel(0): I2C device "LVDSDDC_C:ddc2" removed.

My details:
FujitsuSiemens s6420 Laptop (Intel graphics card)
Ubuntu intrepid - kernel 2.6.27-9-generic

This bug that you point out is not exactly related with thi. Is there any open bug or hint about this?

Thanks!
:popcorn:

> **ollesbrorsa said:**
> Hello,

Glad I could be of assistance :)

I'm afraid I can't help you much on the follow up question. I did a search on "LVDSDDC_C:ddc2" and got a whole bunch of hits. For example: [https://bugs.launchpad.net/ubuntu/+bug/292788](https://bugs.launchpad.net/ubuntu/+bug/292788)

This does not mean it is the same that you are experiencing but it might be a place to start digging.

Br,
ollesbrorsa

---

