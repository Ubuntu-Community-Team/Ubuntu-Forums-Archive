---
title: "Black screen with blinking cursor on boot"
date: 2009-01-19
forum: General Help
---

### Post by sadovsky on 2009-01-19
I had just finished copying a bunch of files off an external onto my main drive (sda1, a 750GB SATA drive). Then, I started downloading Adobe Reader from adobe.com, and at the same time, ran a "du -sh ~/adam/" (which is where I copied files to). Firefox proceeded to die, and I couldn't get it to start again. I also could not delete the partially-downloaded file (got some error about it being read-only, but I don't remember the exact error message). So then I tried to reboot, and the computer would not start up. After the mobo's boot screen, the screen turns black with a white blinking cursor in the upper left. Then it just sits there :( 

I'm pretty sure the problem is not with the mobo/processor/RAM, so I'm wondering if I have some kind of hard drive problem. The BIOS sees both of my hard drives, but I guess something could still be wrong. I tried booting off a Ubuntu CD, and that worked fine, which is perhaps a good sign because I think some things have to be copied to the hard drive for that to work. After booting off the CD I ran "sudo fdisk -l" and saw all the correct partitions on my hard drives. 

I'm really not sure what to do now, though, and I've never seen this kind of problem before. Got any advice for me?

Thanks!
--Adam

---

### Post by sadovsky on 2009-01-19
Update:

This is really weird. I went into my BIOS settings and, just for the heck of it, tried switching around my two hard drives so that the other one would be the "boot" drive. After restarting, my computer starting booting up normally! However, during Ubuntu start-up, it started checking the file system because it detected a bad shut-down, and found some errors. It went into terminal mode, gave me root permissions, and told me to run fsck. I ran fsck on /dev/sda1, which found some errors and fixed them. I restarted again, it checked the filesystem again (no errors this time), and now my computer is back to normal.

Two questions:
1) How could my mobo have flipped my two hard drives on its own? My computer was fine for a week, and then all of a sudden I have to flip the two drives for it to boot properly... how can this happen? I've never heard of anything like it.

2) Should I be worried about this hard drive (it's one week old)? Is there any utility I can use to check my hard drive for problems/defects? Or is it possible that this was a freak occurrence, bug in Ubuntu, etc.?

Thanks,
Adam

---

