---
title: "Stuck! Dell Mini doesn't connect wirelessly after 'updates'"
date: 2009-12-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by rpatch on 2009-12-07
Hello all, new user here. Actually my laptop is my son's, and hes had a notification to do 245 updates for quite a while now.... finally last night I did it. Now there isn't an option to connect wirelessly (wired works fine) which is the only way he connects. 

Is there an effortless way to revert back to the settings I had before this update? Do I need to do a complete reinstall? I'm an Ubuntu-infant, but am technically capable... if someone could steer me in the right direction I'd be forever in debt. 

I think I'm running HH right now, if that sounds right, but I don't know what the update did.

Thanks in advance from a frustrated noob.

-Rob

---

### Post by snowpine on 2009-12-07
> **rpatch said:**
> Hello all, new user here. Actually my laptop is my son's, and hes had a notification to do 245 updates for quite a while now.... finally last night I did it. Now there isn't an option to connect wirelessly (wired works fine) which is the only way he connects. 

Is there an effortless way to revert back to the settings I had before this update? Do I need to do a complete reinstall? I'm an Ubuntu-infant, but am technically capable... if someone could steer me in the right direction I'd be forever in debt. 

I think I'm running HH right now, if that sounds right, but I don't know what the update did.

Thanks in advance from a frustrated noob.

-Rob

Hi Rob, the Broadcom card in your Mini needs a "restricted module" to function. Modules must be compiled separately for each kernel version. My hunch is that your upgrades included a new kernel version, which is why the module is no longer found.

As a temporary fix, you should be able to select the old kernel from your Grub boot menu. That should get you back on line.

It's been a while (pre-Karmic) since I used Ubuntu on my Dell Mini, but in the past, I used System->Admin->Hardware Drivers->Broadcom STA to get it working (you may need to temporarily connect to the internet using wired ethernet). Hopefully a current Dell/Ubuntu user can confirm that this still works. :)

---

### Post by rpatch on 2009-12-07
Wow, that worked great... I spent 3 hours searching online for a fix yesterday and you knocked it out of the park in 5 mins. I owe you a beer.

Thanks again, and problem solved.

-Rob

---

### Post by snowpine on 2009-12-07
> **rpatch said:**
> Wow, that worked great... I spent 3 hours searching online for a fix yesterday and you knocked it out of the park in 5 mins. I owe you a beer.

Thanks again, and problem solved.

-Rob

I was wondering where this beer came from, thanks! 

Dell Mini is great (I have the 9" version) but why oh why did they choose Broadcom for the wireless?

---

### Post by rpatch on 2009-12-07
Hmm, I may have to take that beer back... now when I try to log on, it prompts me to enter my password, I type it in, it thinks for a few, then the window pops back up again, except that the password in the box (when I click 'show password' isn't what I typed, but a bunch of random letters and numbers.

I can still connect wired, and the settings I turned on in the wireless connection part of the hardware manager are still holding. When I click 'Manage Connections' and go to the 'Wireless' tab, it shows my network name in there twice.... one created 7 months ago when I bought it, and the other just created.

I'm again confused, any ideas??

---

### Post by snowpine on 2009-12-07
I'm sorry, but it's been a long time since I ran 8.04 on my Dell Mini... so I can't reproduce the problem to help you more specifically. 

Other than these here forums, I would steer you towards two excellent resources:

[http://www.mydellmini.com/forum/](http://www.mydellmini.com/forum/)
[http://www.ubuntumini.com/](http://www.ubuntumini.com/)

The bottom line is this: Broadcom wireless is a little tricky in Linux. But it works once you set it up, I promise. :)

---

### Post by coffeeaddict22 on 2009-12-08
Hi,
Try ```
lsmod
``` in a terminal and see if ndiswrapper is listed along with wl (wl is the Broadcom STA driver).  If he's upgraded, he may now have two wireless drivers; usually doesn't work too well.

---

### Post by rpatch on 2009-12-09
I did lsmod, and didn't see either of the 'wl' or the 'ndiswrapper' listed. It sees my network, says that the wireless hardware is wrking, but goes through the endless password loop. Frustrating indeed....

---

### Post by coffeeaddict22 on 2009-12-09
Can you post back the output of lsmod?  
Have you tried changing it from an infrastructure to an ad-hoc network?

---

### Post by ugm6hr on 2009-12-09
> **rpatch said:**
> I did lsmod, and didn't see either of the 'wl' or the 'ndiswrapper' listed. It sees my network, says that the wireless hardware is wrking, but goes through the endless password loop. Frustrating indeed....

I actually don't think this is anything to do with Broadcom.

I remember having a similar intermittent issue with Ubuntu 8.04; I think the problem is with Network manager rather than the drivers, since if there was a driver issue, it would not offer any networks at all.

Honestly, I'd suggest just installing a newer version; I'm still on 9.04, which works great, but 9.10 is good too, apparently.

---

