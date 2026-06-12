---
title: "Suspend freeze in HP workstation"
date: 2008-12-09
forum: General Help
---

### Post by jdc.84 on 2008-12-09
I recently installed Ubuntu onto my laptop with a series of faults, but as i really wanted to persist with Ubuntu i went ahead and installed it onto my desktop:  HPxw4600*t workstation

Everything seems to be working fine with one exception:
I can put the system into suspend, but i cannot awake it again. When i do try, all i get is a blank screen.

I have noticed a few other similar threads relating to a few Dell laptops, would anybody have any advice with my HP??

---

### Post by jdc.84 on 2008-12-09
Does anybody have any ideas?????

---

### Post by jdc.84 on 2008-12-10
I have trolled through various threads and found no solution:

[http://ubuntuforums.org/showthread.php?t=786311&highlight=suspend+freeze&page=8](http://ubuntuforums.org/showthread.php?t=786311&highlight=suspend+freeze&page=8)

[http://ubuntuforums.org/showthread.php?t=904633&highlight=suspend+freeze&page=3](http://ubuntuforums.org/showthread.php?t=904633&highlight=suspend+freeze&page=3)

[http://ubuntuforums.org/showthread.php?t=943359&highlight=suspend+freeze](http://ubuntuforums.org/showthread.php?t=943359&highlight=suspend+freeze)


All of which are stating the same or similar problems:
"system will not awake from suspend"

:confused:

---

### Post by jdc.84 on 2008-12-16
>?<

---

### Post by andreasis on 2008-12-16
John!

I've finally come back from vacation, where I had my wireless dongle stolen from my hotel room(can you say awkward?) I'm a bit upset that not a single person has said anything on this issue -- never mind how you must feel.  I will help you with everything that I can. Fortunately you have been able to do without it for a week : )

I'm really glad to hear about your decision to feed Ubuntu to the desktop pc, rather than replacing the laptop right away.

This problem can be either a software issue or a hardware issue --both of which are very likely.
Do you notice any peculiar entries in your /var/log/syslog or /var/log/userlog at/around the time when your computer goes to sleep or when it is trying to wake up?  Post them if you think that they could help.

A hardware issue would be less stressful (for me) to diagnose.  Firstly, I will assume (correct me if I'm wrong) that your HP machine used to go into suspend and wake up without any problems when you had windows running on it.  Do you remember if it would actually turn off when it was suspended, whether the hard disks were halted, whether the power supply shut off?  In your computer's bios, do you have some power settings... ACPI [power states (S1/S2/S3)]

I will go ahead and bug you again to check with HP's website and ensure that you have the latest BIOS.  It is very well possible that a newer bios may prove to be an improvement.

It is my understanding that all components of a computer must (should) be, if not certified, then at least qualified to reach a certain state of suspension.  States and more info: [http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface#Power_States](http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface#Power_States)
A problem with my computer was that the power supply wouldn't handle being suspended, so when the bios boasted an S3 powerstate, where only the ram receives just sufficient power, the power supply would actually shut off completely, thereby destroying the data in the ram.

Suspension is a superb feature and I hope that we can get this sorted out for you in no time.

Please post more info / elaborate / what kinds of options does your bios offer you that may seem related or advantageous toward power management and suspension.

---

### Post by jdc.84 on 2008-12-18
Ah brilliant, thanks for the help. Yea as far as i can see the popularity of Ubuntu is snowballing so i thought it daft to give up now; but on the same note i do not think that it is big enough yet to warrant spending any money on a new comp specifically for ubuntu. The majority of programs i use everyday would require me to use VirtualBox all the time, which seems a little daft as VirtualBox is unable to harness the full power of the computer it's on (a huge disadvantage when using CAD programs and Adobe).

Anyway, thanks for the reply but i am myself away from home till the weekend which doesn't help as that is where my desktop is. I will be able to see what's what when i get back tho.

Thanks again,
John.

---

