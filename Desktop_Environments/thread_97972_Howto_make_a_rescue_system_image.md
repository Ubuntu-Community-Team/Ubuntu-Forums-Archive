---
title: "Howto make a rescue system image"
date: 2005-12-02
forum: Desktop Environments
---

### Post by jrev on 2005-12-02
Hi all,

I am on Ubuntu since a year and I am looking for an easy way to store and restore an operating Breezy installation 

Have you got any idea on the subject ?

I just get the name of bximage which is in the ubuntu packages 

Can it do the job ?

Thanks

---

### Post by akiro.yamamoto on 2005-12-02
I think that there is a utility in the repositories for this....hhhhmmmm
I think it's called the Simple Backup Utility :smile:
I'm not sure if this is exactly what you had in mind, but take a look you may find it very usefull...
Regards

---

### Post by Joeak on 2005-12-02
bximage is for/part of bochs, which is an emulation package, like for running Windows "images" inside of Linux.  I don't think it would help with imaging your machine and restoring it.

I have used Partimage to backup and restore Debian machines, but it's kind of manual (you have to boot off of a live cd for instance) and pretty slow, and you have to either have two local disk partitions (original and to copy to) or you have to have lots of network storage and know how to access it.  But it does work.  I moved my server from one hard drive to another that way.  It's not easy enough for me to schedule it as backups though.  I do scheduled backups of DATA not the entire system.

---

### Post by frodon on 2005-12-02
Look at this thread : [http://www.ubuntuforums.org/showthread.php?t=81311](http://www.ubuntuforums.org/showthread.php?t=81311)

---

### Post by meborc on 2005-12-02
the newest ghost should support linux filesystems... or did i see that in my dreams... don't remember anymore... but ghost was, is and will be the app to use to backup u'r sys... ofcourse you can do it manually like in the thread frodon is pointing at

---

### Post by frodon on 2005-12-02
Are you talking about norton ghost ? If yes i can confirm that the latest version support linux file system, i already perform 3 successful restore with norton ghost so no problem with it !

---

### Post by meborc on 2005-12-02
yep... that was what i was talking about... :D thanks for confirming... i should also look into that soon as my fingers itch to make something nasty with my box... [evil laughter]

---

### Post by jrev on 2006-05-06
Do you know G4L (ghost for Linux) which is a fully free software ?
[http://sourceforge.net/projects/g4l](http://sourceforge.net/projects/g4l)

---

