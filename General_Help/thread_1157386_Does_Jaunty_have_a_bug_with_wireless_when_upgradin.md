---
title: "Does Jaunty have a bug with wireless when upgrading"
date: 2009-05-12
forum: General Help
---

### Post by chiques on 2009-05-12
I recently upgraded to Jauny 9.04 and my wireless configuration is now all screwed up. 

Is there a bug?

---

### Post by nacho32 on 2009-05-12
i would not suggest a upgrade but a fresh install

---

### Post by chiques on 2009-05-12
OK. It's time to break out the 1TB USB drive to backup my docs. I'll post my results.

---

### Post by Old *ix Geek on 2009-05-12
> **nacho32 said:**
> i would not suggest a upgrade but a fresh installI did fresh installs on all of my computers--and wireless no longer worked on any of them.  After much mucking around--which I really didn't have the energy for (having recently had brain surgery)--I gave up and downgraded back to Intrepid.  INSTANT wireless!

---

### Post by chiques on 2009-05-12
decisions decisions....well my notebook isn't much use to me without wireless so I have to do something.

I'll first try to reinstall Jaunty from the 9.04 image. 

If that doesn't work.

Well, time to go back to whatever version I had that actually worked.

---

### Post by RJ12 on 2009-05-12
I used Wubi to install my Ubuntu 9.04 and Wireless instantly worked with no problem. I wonder why if there is just certain compatibility or not. By the way my internet card is a Linksys WUSB54GC. Could it be Wubi. When I first started I Didnt even have to enable it all I did was put in the Wep key and it worked.

---

### Post by chiques on 2009-05-12
> **RJ12 said:**
> I used Wubi to install my Ubuntu 9.04 and Wireless instantly worked with no problem. I wonder why if there is just certain compatibility or not. By the way my internet card is a Linksys WUSB54GC. Could it be Wubi. When I first started I Didnt even have to enable it all I did was put in the Wep key and it worked.

This was my experience with the Ubuntu version before Jaunty

---

### Post by zenithdave on 2009-05-12
Try forcing your router to a  channel below 11 and try again, this problem plagued me for months.

Ubuntu does not enable channels above 11 in Hardy and it took me and a few other people to work out this is the problem. BUT it is in the release notes for Hardy and probably Jaunty.

I have never had a problem with wireless since .

Give it a go you may be surprised ;)

---

### Post by chiques on 2009-05-12
> **zenithdave said:**
> Try forcing your router to a  channel below 11 and try again, this problem plagued me for months.

Ubuntu does not enable channels above 11 in hardy and it took me and a few other people to work out this is the problem. BUT it is in the release notes for hardy.

I have never had a problem with wireless since .

Give it a go you may be surprised ;)

But everything has been working fine up until about 1 week ago when I installed Jaunty. Also, my Windows machines connect to the router just fine.

---

### Post by zenithdave on 2009-05-12
Just give it a go ;)

---

### Post by chiques on 2009-05-12
> **zenithdave said:**
> Just give it a go ;)

Thanks for the tip.

---

### Post by zenithdave on 2009-05-12
There is a fix as AMJ used and it worked there. Im lazy and just tied the router down to channel 1



[http://ubuntuforums.org/showthread.php?t=1087879](http://ubuntuforums.org/showthread.php?t=1087879)

---

### Post by chiques on 2009-05-12
> **zenithdave said:**
> There is a fix as AMJ used and it worked there. Im lazy and just tied the router down to channel 1



[http://ubuntuforums.org/showthread.php?t=1087879](http://ubuntuforums.org/showthread.php?t=1087879)


Ironically 8.10 worked pretty much flawlessly for me.

---

### Post by joey-elijah on 2009-05-12
> **chiques said:**
> Ironically 8.10 worked pretty much flawlessly for me.

9.04 has been flawless for me, no pretty much.

---

### Post by zenithdave on 2009-05-12
Im far from up on the issue but i suspect early versions had it enabled then some organisation like the Wireless regional regulation body sent a few heavy letters and it was switched off by default????

Someone put me out of my misery :o

---

### Post by chiques on 2009-05-13
Hello ladies and gentlemen, 

This issue has been resolved. Out of all of the suggested recommendations, none of them worked. 

Here is the fix for my specific problem.


1. Shut down the notebook (see 2a if you have a logic switch)

2. Turn off the wireless card (yes, switch it off)

2a. If you have a logic switch, power if off before you shut down.

3. Power up the notebook

4. Boot to the desktop (with the wireless card off)

5. Power on the wireless card through the physical switch. Wait a few seconds and you should see the indicator light on the notebook register as "on". You will then see the bar icon begin it's search for wireless networks and hard drive activity. 

6. At this point the local wireless network will be detected and if already configured it will connect to it.

It seems to be some sort of initialization problem.


Thanks for everyone's input.

---

