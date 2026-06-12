---
title: "External HD with ext3 File System Question"
date: 2009-05-06
forum: General Help
---

### Post by youngheart80 on 2009-05-06
Hey all. 

My old computer which I had been planning to replace next month just died on me - haven't yet had the chance to fully troubleshoot it, but sufficeth to say that it won't power on.

I'm hoping to get access the files on the hard drive in the interim period before I get my new computer (mostly my /home directory).  I have an external enclosure that I wanted to use to get access via USB, but having not had a ton of experience yet, I thought I'd ask first before I try to prevent breaking anything.

So, with that lead it:
Will it cause any problems to mount a hard drive with an ext3 file system in an external USB enclosure?

My guess is that it won't but hoping someone can confirm.

Thanks

---

### Post by LinuxRules1 on 2009-05-06
You shouldn't have any problems mounting the drive. I have done it before. It may prompt you for your root password when you mount it.

---

### Post by monsterstack on 2009-05-06
ext3 won't cause any problems with the external device, if that's what you mean. Compatibility with Windows would be your only problem I think.

---

### Post by dabl on 2009-05-06
If you are running Linux, power up the external drive/enclosure first, then plug in to the USB connector, and whatever partitions on that drive are readable by Linux should pop up in the "notifier" and be available.

If you're running Windows when you do this maneuver, you'll need the Windows ext2/3 driver installed before Windows will read the ext3 partition.

If you hope to access it more than one time, don't forget to right-click and "eject" or "safely remove" before you yank out the USB connector -- ext3 is a journalling filesystem and needs to flush its writes to disk prior to being disconnected, or you risk data corruption.

---

### Post by youngheart80 on 2009-05-06
Thanks all.  That's what I figured.  I will be accessing them through Windows on my friend's laptop and had already been looking at the ext2fs drivers.

---

### Post by monsterstack on 2009-05-06
[ext2 IFS for Windows]("http://www.fs-driver.org/index.html") [fs-driver.org] is said to be quite good. It works with ext3 partitions although it recognises them as ext2. You'll also be annoyed at just how many .something files and folders there are in your home directory that *aren't* hidden on Windows.

---

