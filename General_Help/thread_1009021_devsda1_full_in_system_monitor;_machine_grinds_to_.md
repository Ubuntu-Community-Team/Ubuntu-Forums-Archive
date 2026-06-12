---
title: "/dev/sda1 full in system monitor; machine grinds to halt; basic properties different"
date: 2008-12-12
forum: General Help
---

### Post by oneafrikan on 2008-12-12
Hey All,

OK so last night I was doing an rsync backup, as you do on a Thursday evening, and rsync stalled saying something about not enough memory... 

So I had a look at my filesystems (/ partition for OS; and /home partition for my stuff) and it says that /dev/sda1 is 100% full.

result is machine is grinding to a halt, and apps are shutting down...

df command in terminal says the same thing.

however, when i use "Properties" (right click on directory names) it shows the whole of / as only 5.2GB, on a 14.4 partition...

touch /forcefsk => doesn't seem to have done anything:
[http://ubuntuforums.org/archive/index.php/t-775653.html](http://ubuntuforums.org/archive/index.php/t-775653.html)

i don't seem to have any masive log files:
[http://ubuntuforums.org/showthread.php?t=866445](http://ubuntuforums.org/showthread.php?t=866445)

googling for "/dev/sda1 full" doesn't seem to yield much

so something is fishy methinks... and I'm wondering if any of the fine people here could help? ;-)

Thanks in advance!

---

### Post by oneafrikan on 2008-12-12
OK, seem to have fixed it...

Found this thread:
[https://answers.launchpad.net/ubuntu/+question/11825](https://answers.launchpad.net/ubuntu/+question/11825)

which made me look in the /media directory... which showed that my external disk drive I was rsyncing to yesterday, was still mounted (which it wasn't).

Doing a check of the size of the external disk drive mount directory, showed 72kb... so I deleted it just in case with sudo rm -R WD_80, which took a wee while to do...

Then I took another look at the disk in the partition viewer, and it's back to normal...

So seems that the disk was never fully unmounted, or something like that...

Hope that helps someone someday!!

---

