---
title: "Dell Latitude D600 fails to boot on battery only 75% of the time"
date: 2007-10-30
forum: Dell  Ubuntu Support
---

### Post by f2racer on 2007-10-30
I'm seeing the same problems reported by others on this forum:

[http://ubuntuforums.org/showthread.php?t=549319](http://ubuntuforums.org/showthread.php?t=549319)
[http://ubuntuforums.org/showthread.php?t=552410](http://ubuntuforums.org/showthread.php?t=552410)

I've disabled the parallel port in BIOS as suggested in the first thread, but the system still hangs approximately 75% of the time I try to boot without the laptop plugged in. Does anybody know what else I can do, or what log files I should be looking at? I'm new to Ubuntu...

Thanks!

---

### Post by bluedragon436 on 2007-10-30
I have seen this a few times on here with different model laptops....I have not personnally had this problem, but after doing some research have found that apparently this does happen with a few models every now and again even with Windows installed...  just not as often

---

### Post by f2racer on 2007-11-05
I've had both Windows 2000 Pro and XP Pro installed on the same laptop without issue.

I did get an answer on the linuxquestions forum that pointed to a change that needs to be made to the /etc/pcmcia/config.opts file to remove the following from the file:

port 0x800-0x8ff

I found more info here:

[http://www.marlow.dk/site.php/tech/dell_latitude_d600](http://www.marlow.dk/site.php/tech/dell_latitude_d600)

I plan on retrying Ubuntu to see if this fixes the issue. I'll post my results.

Thanks!

---

### Post by f2racer on 2007-11-08
Removing the port line from the /etc/pcmcia/config.opts file had no impact. I got so frustrated that I installed opensuse on the laptop, but it too failed to boot on battery. After a lot of swearing, I figured out that the problem was due in part to the ndiswrapper IRQ conflict. After a while, I found the fix here:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/16247]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/16247")

It appears that Dell put in a *Quick Boot* feature in it's bios for a setting called *Boot POST*. It is what the default is and works fine with Windows. I changed this to *Thorough* and now opensuse boots without issue from battery. I'm pretty sure the same would be true for ubuntu.

Just thought I'd contribute what I found.

Thanks!

---

### Post by Perpetual on 2007-11-08
I have a Dell D600 also, no problems at all.  I do not have my laptop with me at the moment but I have never changed the bios settings.  Wonder if that is not set by default.

Edit: I grabbed my laptop and it was set to Boot Post: Minimal.  Again, have never had a problem.  Just booted it with 12% battery power and it runs fine.

---

### Post by f2racer on 2007-11-09
I wonder if this occurs only with specific configurations or with certain versions of the bios.  I'm running A16 on mine.

> **Perpetual said:**
> 
Edit: I grabbed my laptop and it was set to Boot Post: Minimal.  Again, have never had a problem.  Just booted it with 12% battery power and it runs fine.

---

### Post by Perpetual on 2007-11-09
> **f2racer said:**
> I wonder if this occurs only with specific configurations or with certain versions of the bios.  I'm running A16 on mine.

A16 here as well.

---

