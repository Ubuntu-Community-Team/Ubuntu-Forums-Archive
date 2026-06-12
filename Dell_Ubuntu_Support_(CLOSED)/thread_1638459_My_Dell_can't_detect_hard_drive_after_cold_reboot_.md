---
title: "My Dell can't detect hard drive after cold reboot - i'm desperate"
date: 2010-12-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by nemesis.design on 2010-12-05
I everyone I'm new on this forum.

Something happened to me right now that really scares me.. I was working when my laptop dell xps got frozen. I tried rebooting it but it didn' work out so I tried to follow the suggestion in this post:

[http://ubuntuforums.org/showthread.php?t=617349](http://ubuntuforums.org/showthread.php?t=617349)

But it didn't work out or I think I was not able to do it properly until I pressed alt+sysrq+B and the system went for reboot but then when it was back it never worked again!

I did a diagnostic test and the result I get is "NO DRIVE DETECTED"

I tried booting from Ubuntu on CD and.. initially the linux splash screen appears but when I try to start the ubuntu CD nothing happens.. the screen becomes black with the cursor on the top left and nothing happens.

Please help me.. When I pressed those keys I didn't really know what I was doing...
What might have happened?

Is it possible that I broke my hard drive??? If yes I would have lost a month of work...

I don't know what to do.. my dell is new.. I bought it in february.. at the moment I'm in Ibiza ... which is an island in Spain and I don't really trust to go to shops here as they might invalidate the warranty or break it even more..

What do you think?

---

### Post by krunalpatel on 2010-12-06
Does your BIOS recognize your hard drive?

---

### Post by nemesis.design on 2010-12-06
No.

---

### Post by nemesis.design on 2010-12-06
It also does some beeping sound when I turn it on.

When going to the BIOS setup it says:

Fixed HDD: [None]
e-SATA     None


If I press enter on "Fixed HDD" it shows an empty page and on the right is written "All items on this menu cannot be modified in user mode. If any items require changes, please consult your system Supervisor."

---

### Post by krunalpatel on 2010-12-06
open the back panel of ur laptop (underneath) and remove / reinsert your hard drive. Maybe something is loose or you may have to have it replaced. Seems like a hardware issue

---

### Post by nemesis.design on 2010-12-06
> **krunalpatel said:**
> open the back panel of ur laptop (underneath) and remove / reinsert your hard drive. Maybe something is loose or you may have to have it replaced. Seems like a hardware issue

Do I have to unplug and replug the cables?
The hard drive looks quite small and delicate.

Will I invalidate the warranty?

---

### Post by pricetech on 2010-12-06
It does sound like you have a dead hard drive.  Its death is probably why your computer locked up in the first place.

If you don't feel comfortable handling the drive, don't do it.  Reseating it may or may not help, but if you're nervous about it, it's best not to.

If your Dell is still under warranty, contact Dell Support for a replacement drive.

---

### Post by krunalpatel on 2010-12-06
> **nemesis.design said:**
> Do I have to unplug and replug the cables?
The hard drive looks quite small and delicate.

Will I invalidate the warranty?

It should not. Call Dell

---

### Post by nemesis.design on 2010-12-07
You're right. I removed it from my laptop and connected to my desktop computer .. same beeping .. my desktop couldn't see it.
By examining in detail the surface I can see some very little scars.
Now I wonder how the hell is this possible? Is not even 1 year old.

---

### Post by ugm6hr on 2010-12-07
> **nemesis.design said:**
> Now I wonder how the hell is this possible? Is not even 1 year old.

Electronic components fail. That's why warranties are used....

---

### Post by jwbrase on 2010-12-07
> **nemesis.design said:**
> You're right. I removed it from my laptop and connected to my desktop computer .. same beeping .. my desktop couldn't see it.
By examining in detail the surface I can see some very little scars.

Wait, what surface? The outside of the drive? That doesn't mean anything. 

Or did you open it up (the *drive*, not the computer) to take a look at the disk platters? That will probably void the warranty, although if the disk is scratched it would indicate that you did have a head crash.

> 
Now I wonder how the hell is this possible? Is not even 1 year old.

Actually, for a lot of equipment, the two most likely times for a device to fail are when it's brand new and when it goes beyond its design lifetime. See [http://en.wikipedia.org/wiki/Bathtub_curve](http://en.wikipedia.org/wiki/Bathtub_curve)

---

### Post by Xial on 2010-12-11
> **nemesis.design said:**
> I everyone I'm new on this forum.

Something happened to me right now that really scares me.. I was working when my laptop dell xps got frozen. I tried rebooting it but it didn' work out so I tried to follow the suggestion in this post:

[http://ubuntuforums.org/showthread.php?t=617349](http://ubuntuforums.org/showthread.php?t=617349)

But it didn't work out or I think I was not able to do it properly until I pressed alt+sysrq+B and the system went for reboot but then when it was back it never worked again!

I did a diagnostic test and the result I get is "NO DRIVE DETECTED"

I tried booting from Ubuntu on CD and.. initially the linux splash screen appears but when I try to start the ubuntu CD nothing happens.. the screen becomes black with the cursor on the top left and nothing happens.

Please help me.. When I pressed those keys I didn't really know what I was doing...
What might have happened?

Is it possible that I broke my hard drive??? If yes I would have lost a month of work...

I don't know what to do.. my dell is new.. I bought it in february.. at the moment I'm in Ibiza ... which is an island in Spain and I don't really trust to go to shops here as they might invalidate the warranty or break it even more..

What do you think?

If you received error 2000-0141 from the diagnostic that I think you ran, and if you haven't already done this, assuming you still have warranty left:
Please contact Dell Technical Support for your area.
Tell them the following:
Ran Dell Diagnostics.
DST Failed: Error 2000-0141, Hard Drive not detected.
Reseated hard drive: No change.
Moved Hard drive to known good system: no change.

Request the drive that they should order for you to be blank (so you can install a fresh copy of Ubuntu on it).

:)

---

