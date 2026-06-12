---
title: "Strange GRUB Error 18"
date: 2006-07-10
forum: Desktop Environments
---

### Post by blip on 2006-07-10
I've been having an odd GRUB problem.  I run a dual boot system and whenver windows crashes GRUB gives me an error 18 until I shut the system completely down and reboot.  After powering down and rebooting it generally works just fine but occasionally it needs a second power cycling to get it working.

I've heard that Error 18 often results from an old bios but I'm using one released this year so I can't imagine that is the problem.

Any thoughts?

---

### Post by EnderTheThird on 2006-07-10
I think that's the same error I got when I wiped my Ubuntu HDD while still having GRUB installed on the MBR on my primary drive because the GRUB menu was no longer present and/or accurate.  This is probably a bit of a stretch, but maybe one of your HDDs isn't initializing fast enough when you just do a plain restart as opposed to a full power cycling.  It kinda makes sense in my head (heh, if that's at all comforting), seeing as if one or more of your HDDs isn't ready when it checks GRUB, it would return the same error as my computer did when my Ubuntu drive was no longer present.  You could check through your BIOS and see if there's a manual setting for how long your computer should delay trying to access the HDDs before continuing to boot.  Hell, it's worth a try, so if you find that setting (not sure if they still have it with SATA setups) let me know if that helps you.  Good luck!

---

### Post by Appolusionist on 2006-07-10
> **blip said:**
> I've been having an odd GRUB problem.  I run a dual boot system and whenver windows crashes GRUB gives me an error 18 until I shut the system completely down and reboot.  After powering down and rebooting it generally works just fine but occasionally it needs a second power cycling to get it working.

I've heard that Error 18 often results from an old bios but I'm using one released this year so I can't imagine that is the problem.

Any thoughts?

I did a quick search in the forums and found the following:
[http://ubuntuforums.org/showthread.php?t=208833]("http://ubuntuforums.org/showthread.php?t=208833")
and I also found this guide on Gentoo's forums:
[http://www.gentoo.org/doc/en/grub-error-guide.xml]("http://www.gentoo.org/doc/en/grub-error-guide.xml")

---

### Post by blip on 2006-07-10
Interesting thoughts Ender (good name too).  

The difference between this and most GRUB error 18s is that in most cases (according to my reading) it is a constant problem not intermittent.  That's what makes it strange.

---

### Post by blip on 2006-07-11
I may have found a possible solution.  It struck me that I hadn't checked the internal connections on the system since I had moved it to its present location.  Sure enough, the SATA connector to the mobo had worked itself slightly loose.  Not bad enough to disconnect the harddrive but enough that it was VERY easy to remove.

Anyway, I reseated it and the problem seems to have gone away.  I've intentionally crashed windows about five times and the error has yet to reappear.  Of course, it was quite intermittent to begin with so this might be a false solution. (Crosses fingers)

So my theory is that the cable was making an imperfect connection and thus was (perhaps) delivering bad data to GRUB on some occasions.  Why these problems only occured when windows crashed still vexes me however and is the one reason why I'm skeptical that I've really found the cure.  Well we shall see I guess!

---

