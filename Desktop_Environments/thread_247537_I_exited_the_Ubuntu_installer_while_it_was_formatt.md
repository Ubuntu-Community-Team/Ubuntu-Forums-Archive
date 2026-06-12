---
title: "I exited the Ubuntu installer while it was formatting..."
date: 2006-08-30
forum: Desktop Environments
---

### Post by mullenrbock on 2006-08-30
I made a biiiiiig mistake while installing Ubuntu.

I just installed a new 500 GB hard drive (sata), and I went to install Ubuntu on it, and I got to the point where it started to install.

Unfortunately, I am clumsy, and pressed the exit button. Whoops.
I knew that this was going to be a problem, but I didn`t realize the proportions of it; I put in a Kanotix-64 live CD and checked the partitions of that drive:
There were three partitions, the first being ext3, started at 0.03 MB and ended at 460 GB; the second being called "extended" and was 5.65 GB, and under that was a linux-swap, I don`t remember the exact size of that.
So I decided to see if I could delete the partitions and recommit the drive clean without any filesystems on it. I successfully got the first partition to reformat, but I could not delete the other two (the system refused to unmount them) and could not reclaim the entire drive from start to finish.
I decided to try reinstalling Ubuntu, since I could delete all drive information with the Ubuntu installer. Ubuntu installed fine, and I rebooted my computer. Ubuntu did not boot, even though I was on the correct hard drive. I checked it with Kanotix again, and this time the only thing that changed was that the former linux-swap partition was now "unknown" format.
](*,) ](*,) ](*,) ](*,) ](*,) ](*,) 

If anybody would be so nice as to help, it would be GREATLY appreciated.

---

### Post by mullenrbock on 2006-08-30
Is there a way to just delete EVERYTHING on the drive? If so, how would I do that?

---

### Post by The Seeker on 2006-08-30
Use [DBAN](http://dban.sourceforge.net/) to wipe the HDD (will take a few hours) then run the Ubuntu installer again.

---

### Post by mullenrbock on 2006-08-30
> **The Seeker said:**
> Use [DBAN](http://dban.sourceforge.net/) to wipe the HDD (will take a few hours) then run the Ubuntu installer again.

Excellent. Thank you.

---

### Post by mullenrbock on 2006-08-31
> **The Seeker said:**
> Use [DBAN](http://dban.sourceforge.net/) to wipe the HDD (will take a few hours) then run the Ubuntu installer again.

I just used the quick-wipe method, and I still got the same thing. Is it even remotely possible I really messed up my hard drive physically, or should I just use a higher-level wiping method?

---

