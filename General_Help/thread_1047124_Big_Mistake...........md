---
title: "Big Mistake.........."
date: 2009-01-22
forum: General Help
---

### Post by superpink99 on 2009-01-22
Hello, ok heres the scenario i have a dual boot  laptop (xp and ubuntu)
Now when i scanned my xp with bitdefender and let it delete the ones it detected, guess what the next time i reboot in xp it just restarts again and again, good news is that my ubuntu is still working.

Can anyone please help me with this, how do i fix my xp without disturbing my ubuntu? i really need to retreive my files in xp, oh one thing more i used to access my xp drive in ubuntu but now it can't mount the drive.

need help please........

---

### Post by Rainstride on 2009-01-22
got to love them system32 viruses(sigh..). you have to mount the drive inside windows first and use the safely dismount thing. you don't happen to have a econd HD in your comp or a external do you?

---

### Post by hal8000 on 2009-01-22
Probably the reason why the NTFS volume cannot be read is because it has been marked as a dirty volume.

Post the output of

sudo fdisk -l


then

sudo apt-get install ntfsprogs


May be able to repair the volume with ntfsfix and then mount it and recover your data into Ubuntu

---

### Post by superpink99 on 2009-01-22
i do have an external hard drive ( fujitsu 300g) but the one that ubuntu and xp uses is only one drive i partitioned.

---

### Post by hyper_ch on 2009-01-22
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

