---
title: "Wake from suspend unexpectedly"
date: 2009-01-29
forum: General Help
---

### Post by peppergrower on 2009-01-29
I have Ubuntu 8.10 on a Dell Inspiron E1505 (equivalent to an Inspiron 6400).  I've had issues with my laptop waking from standby mode unexpectedly.  The times I've noticed seem to fall into two categories:

1) It wakes when I unplug either (a) the power cord, or (b) the Ethernet cord.  I've noticed it happen multiple times that simply unplugging one or the other causes my computer to power back up.  It seems to go back to sleep after about a minute or so (if I don't open the lid).

2) It wakes up for no apparent reason at all.  Sometimes, without any action on my part, my laptop will wake up.  This is a huge, huge problem, as (a) it can be inside my bag and I'm worried about overheating, and (b) I've had it run the battery down to 5%, until it finally shut itself down.  (This despite having my power management preferences set to suspend after 20 minutes of inactivity on battery power.)

Is there a solution to this?  This behavior is causing me rather significant concern, and I'd love to get it resolved.

---

### Post by heluani on 2009-03-25
I have the same problem on a MacBook Air 2,1. I noticed that it wakes also when I move/shake the computer, that's why I thought it had to do with some accelerometer or something like this.

R.

---

### Post by peppergrower on 2009-03-25
Yeah, I've wondered about that too.  If the sensor that detects the lid being closed is faulty, I could see that happening.  It's possible that something like this explains the random turning on when I don't do anything at all.

However, with mine, I've also seen this happen when the laptop very definitely didn't move--not even a little bit.  Somehow just the act of unplugging the power cord or Ethernet cable (without jostling the laptop) makes it turn back on occasionally.

---

### Post by heluani on 2009-03-25
check your /proc/acpi/wakeup to see what is allowed to wake your computer up. I'm really disturbed by this. I can leave the laptop sleeping all night. But as soon as I move it the next morning it wakes up.

R.

---

### Post by peppergrower on 2009-03-25
Good suggestion.  The only two that are marked enabled are LID and PBTN, which I assume is the power button.

---

### Post by heluani on 2009-03-25
yep, then that's not the issue :)

---

### Post by The_Doc_tor on 2009-03-27
I have an interesting problem and this thread was the closest I could come to mine.
I installed Ubuntu 8.10 onto my P4i65G P4 2.4ghz 80Gig PC with no problems.
I installed it under Windows XP environment & that could be my problem. Drive C: 80G Win XP SP 3 Drive D: 80G Ubuntu 8.10.
When I shutdown the computer from my session in Ubuntu the motherboard gives a healthy Beep & the whole system re-boots instead of shutting down.
I know my problem is not the same but any sugestions would be greatly appreciated.

---

### Post by heluani on 2009-06-04
Upgraded the kernel to 2.6.29.4 and solves the issue for me. Though there are some packages from mactel PPA that I can't use anymore, haven't tested if those were responsible for the wake-ups.

R.

---

