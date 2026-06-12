---
title: "volume boost"
date: 2006-03-30
forum: Desktop Environments
---

### Post by vidak on 2006-03-30
It's not a great problem, but it would be nice, if somebody could help... 
On my laptop the volume is a bit low, even if all the mixer bars are on the maximum value, so it's a bit quiet at a noisy place.
Is there a way to "boost" the volume? it seems that under window$ it's a bit louder...

Thx,

Chris

---

### Post by jamesford on 2006-03-30
dont nkow if u ahve tried alsamixer, but if u havent type alsamixer in a terminal and fiddle around with the settings. it may be that u need to unmute some stuff. this is done with the 'm' key iirc

---

### Post by vidak on 2006-03-31
[QUOTE=jamesford]dont nkow if u ahve tried alsamixer, but if u havent type alsamixer in a terminal and fiddle around with the settings. it may be that u need to unmute some stuff. this is done with the 'm' key iirc[/QUOTE]

I've checked all the mixer settings, both in kmix and in alsamixer.
The problem is not that the volume level is so low that I couldn't hear anything - just I find the maximum available volume a bit low...

---

### Post by vidak on 2006-04-16
If somebody has the same problem, here is a solution for watching videos:
mplayer has an option "-softvol-max" which can be set eg. 500, so the maximum volume will be 5times louder...
Any other ideas?

---

### Post by arif_moin on 2007-10-04
Yea. I noticed the same issue on my laptop. Can hear sound after maxing all settings, but still the volume is a bit on the "timid" side.

I just plugged in a good set of earphones on my lap and I'm satisfied so far. Sorry dude...I'm a rookie myself. This is the most "OOTB" solution that worked...

---

### Post by cwhitehouse on 2007-10-04
I'm also having an issue on my T61.  So far I haven't found solution either, but I will keep monitoring this thread.

---

### Post by drfox on 2007-10-04
Same problem on a Toshiba. Monitoring thread for a fix

---

### Post by CheesyPuffs144 on 2007-10-05
This worked on my T60, so a possible solution.

Go into System > Preferences > Sound and click on some of the Test buttons. I had some music playing at the moment while I was messing around and I ended up waking up all my roommates.

---

### Post by vidak on 2007-10-05
I have posted a bug report to Ubuntu, the site is here
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/112218](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/112218)
The last post says that "This bug does not meet the criteria for a stable release update and is being marked as Won't Fix for this particular version of the kernel." However, it might happen that Gutsy will fix the bug (I doubt that, since it's present since Dapper as far as I remember). I'll give it a try soon... You could check the new version too, and if it won't bring us salvation - could you please attach a few lines to this bug report with your case?

Thanks,

Chris

---

### Post by Sapphiron on 2007-12-29
I also have the same problem on my HP 530.

Volume is good in Vista, and normal Ubuntu sounds.  The problem comes in when playing in Totem.

---

### Post by needhelpplease on 2008-07-10
I have the same problem on my laptop.  It makes movies unwatchable when using the Dragon player.  There's an easy "solution": go to the command line and use:

mplayer -softvol -softvol-max 1000 dvd://1

But this is stupid; we should not have to use a command line mplayer to be able to hear videos.  Why even bother to have Dragon and this stuff if there's no way to hear the audio track?

There should really be a volume boost option within Dragon.

---

### Post by a94060 on 2008-07-15
maybe there needs to be a boost feature built in. a gui version of the softvol would really help so we would not need to use the command line each time.

---

### Post by needhelpplease on 2008-07-19
> **a94060 said:**
> maybe there needs to be a boost feature built in. a gui version of the softvol would really help so we would not need to use the command line each time.

There needs to be a GUI control that does what softvol / softvol-max do.  This isn't a "it would be nice", it is, "we need to have this".  On the last few laptops I've had, I've always had to use Mplayer from the command line to be able to hear the movie.  On desktops, it's not a problem because the speakers are much louder.

---

### Post by xnevermore on 2008-07-21
I would also like to see a solution for this.

Card: HDA ATI SB
Chip: Realtek ALC268

---

