---
title: "Wireless networking not working on 1420N"
date: 2007-08-31
forum: Dell  Ubuntu Support
---

### Post by Kalli on 2007-08-31
I'm sure there are other threads that address this because I've read at least one, but I couldn't find it.

I just got a Dell 1420N laptop and the wireless worked just fine when I started the computer for the first time. But then I shut down and when I turned it back on it Ubuntu can't find my wireless card (or something like that)! I tried everything and eventually I even reinstalled Ubuntu. But even then it still couldn't find the wireless! Common! That's just stupid!

Anyway, does anyone know what the bug is and, more importantly, know how to get the wireless connection back on?

It would seem that this is one of those things that really should work.

---

### Post by kuja on 2007-08-31
I do believe that's one of several things that didn't work "out of the box". Dell  had to apply some fixes so that everything would work. If you want to do a fresh install, you'll have to apply those fixes manually. Check the first page or two in this subforum, it's one of the things mentioned.

On a side note, the wireless works out of the box on Gutsy Tribe 5.

---

### Post by Kalli on 2007-09-01
Well, it did work out of the box, it just stopped working. When I re-installed, I did it from the Grub menu and it reverts to "factory settings" so I don't see why it shouldn't work again.

I don't see where this fix is mentioned either, if you could be more specific that would be nice...

---

### Post by Kalli on 2007-09-01
I tried plugging in a usb wi-fi and that worked fine. Then I unplugged it and a few minutes later I plugged it back in, at which point the network manager apparently couldn't find it. Great.

Then to top it off, at that point my keyboard stopped working, completely. So I decide to reboot, guess what, the damn thing's frozen!

Ain't that a blast!?

I'm just gonna install Windows XP, it may suck but at least it works.

---

### Post by Kalli on 2007-09-01
Really? No one?

---

### Post by kuja on 2007-09-01
The freezing is almost definitely do to a bug and/or memory leak. 

With regards to the wireless it's really hard to tell, perhaps network manger is just being a pain in the butt, will it let you connect with a manual config?

---

### Post by Kalli on 2007-09-01
No, it doesn't seem to find the wireless module at all...

---

### Post by JohnnyC44 on 2007-09-02
I just had this same problem on my E1505n after installing the updates this weekend.  Go to System ==> Admin ==> Network.  Highlight the Wireless Connection and click on Properties.  Check the Roaming Mode box.  Worked for me.

---

### Post by Kalli on 2007-09-02
I'd love to be able to click properties of the wireless connection, but it doesn't show that I have any anymore!

---

### Post by Kalli on 2007-09-04
Well, I talked with a Dell representative. He couldn't help much. "Please let me know which operating system are you using (Vista or XP)?"

Then he told me I needed to update the drivers to fix the problem and for that I needed to contact Dell Ubuntu support... so he gave me a phone number!

He might as well have told me to get a priest on the issue...

---

### Post by perryrt on 2007-09-04
For what it's worth, I started having problems with wireless after downloading updates this weekend too.

In my case, I could still "see" the card, etc, but it wasn't connecting to my home router.

What I found was if I went to the "manual network configuration" mode (click on the network icon in the upper right bar), then in the Network Settings dialog box, I could select another wireless setup (i.e. one of the other places I had saved.) The system would give me the "applying network settings" wait box, and (not surprisingly) it wouldn't find the network. The key is, though, that I could then apply the settings for my home router, and it would "lock on" no problems. I'm using it now.

Related to this, however, is that my boots are taking longer and seem to be having trouble with the network adapters upon startup. So I'm thinking that there's some sort of problem with the new updates.

Not quite sure where to go from here....anyone know if I should be providing a printout of something? Or perhaps we should be doing this on the Dell board rather than the Ubuntu one?

---

### Post by notwen on 2007-09-04
> Related to this, however, is that my boots are taking longer and seem to be having trouble with the network adapters upon startup. So I'm thinking that there's some sort of problem with the new updates.

Do you happen to notice the screen flicker briefly between the "Ubuntu Loading" screen and the start of GDM?  I get this short moment where I am able to view my machine starting the various services and something fails prior to GDM kicking in, it fail right before GDM starts and I can't figure out which service it is.   I'm having similar issues to those you've mentioned above and am wondering if my "failed service" is related.  ANyone knwo of anyway I can view logs of my startup services?

---

### Post by deserthowler on 2007-09-05
> **notwen said:**
>  ANyone knwo of anyway I can view logs of my startup services?

at the command line type:

dmesg | less

and that will give you the start up messages

My 1420n is working fine.  Which components do you have?  Mine has the ipw3945 wireless card.

Earl

---

### Post by Kalli on 2007-09-05
Yep, I think that's the only card sold with it. It worked just as it should the first time I used the computer, but since then it hasn't seemed to find the card.

---

### Post by notwen on 2007-09-05
> at the command line type:

dmesg | less

and that will give you the start up messages

That didn't bring up what I was looking for.  I'm looking for logs that may show 

Starting BLAH                                   [OK]
Starting BLAH01                               [failed]

or something similar.

---

### Post by notwen on 2007-09-05
This [thread]("http://ubuntuforums.org/showthread.php?t=436906") would be more what I'm looking for, I'll see if I can narrow down which service is failing and post back if it has anything to do w/ my wireless not picking up upon startup.

---

### Post by sciurus on 2007-09-06
Any services that fail to start during boot will hopefully write an explanation to */var/log/messages*. If you want to see messages during startup, remove *quiet splash* from the boot options in grub. You can do this in */boot/grub/menu.lst* or by hittting *e* at the grub prompt during boot.

*ifconfig -a* should list all network interfaces in your system. If one fails to show up, try to load the kernel module responsible for it with *modprobe -v* followed by the name of the module, then check *dmesg | tail*

---

