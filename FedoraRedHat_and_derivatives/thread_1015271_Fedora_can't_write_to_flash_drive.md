---
title: "Fedora can't write to flash drive??"
date: 2008-12-18
forum: Fedora/RedHat and derivatives
---

### Post by CompBio on 2008-12-18
I realize this isn't a Ubuntu issue, but I really don't want to join the Fedora groups if I don't have to.  I'm hoping there's a guru here who can explain what's happening.

I don't have fast internet at home, so I took my flash drive to school to grab two sequences of YouTube videos (a set of 5 and another set of 6) to play at home on my Ubuntu laptop (see, not completely off-topic).  I downloaded 11 videos to the Fedora machine at school, checked their file sizes (each one around 40MB) and then copied them to my 2GB flash drive, monitoring the progress indicator to be sure there were no problems.

I brought the drive home and went to copy the videos to my laptop, only to discover that the file sizes for 7 out of the 11 videos on the drive were 0!  (Yes, I should have checked the file sizes on the flash drive while I was at school.)

What the heck would cause this?  Why would Fedora report copying each file (and take the usual amount of time to transfer them) when only a few of them actually transferred?

I don't have any problem with this flash drive between my Ubuntu machine and my (ugh) Windows machine.  I just now copied about 1.8GB of stuff back & forth just to test.  It only seems to be Fedora that can't handle a simple file transfer.  WTF? :mad:

---

### Post by Crafty Kisses on 2008-12-18
There's a couple things you can do, plug it in, and post the results of this command:
```
lsusb
```
You can also run the following while it's connected, post the results of this command:
```
ls -l /dev/disk/by-id
```

---

### Post by Duck2006 on 2008-12-18
If you don't get the info that you need go to
[www.linuxquestions.org](www.linuxquestions.org) and search there for your answer there.


[http://www.linuxquestions.org/questions/linux-newbie-8/how-to-mount-usb-flash-drive-in-fedora-611239/](http://www.linuxquestions.org/questions/linux-newbie-8/how-to-mount-usb-flash-drive-in-fedora-611239/)
[http://fedoraproject.org/wiki/FedoraLiveCD/USBHowTo](http://fedoraproject.org/wiki/FedoraLiveCD/USBHowTo)

---

### Post by Bachstelze on 2008-12-18
Moved to the Fedora/RH section.

---

### Post by Duck2006 on 2008-12-18
[http://fedoraproject.org/wiki/FAQ](http://fedoraproject.org/wiki/FAQ)

---

### Post by tgalati4 on 2008-12-18
Writes to flash drives are cached and performed in large blocks.  If you pull the drive early, you won't get all the files.

---

