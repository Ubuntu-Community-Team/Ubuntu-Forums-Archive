---
title: "8gb of hard disk space has dissapeared"
date: 2009-04-01
forum: General Help
---

### Post by icarid_17 on 2009-04-01
**[[COLOR="Red"]SOLVED[/COLOR]]**

hello, around 6 o'clock pm, i had 8gb of space in my home folder, now i have 64 kb, or at least my file manager thinks i do, i really don't know what happened, the only thing i have done since then is burn an iso to several different disks (it was RiP: A Remix Manifesto, which is a really awesome open source movie) and install a package through synaptic (which took about 10 seconds to download, which, because of the piss-poor state of Internet competition here in Canada and the slow bandwidth speeds come with such a condition means that it was definitely  was a small package). i tried to download something small (a youtube video) which didn't work, so it seems that its not just the file manager that thinks that i am seriously short of space. anyway, i hope someone can help me. by the way,i am using Ubuntu Ultimate 1.9

---

### Post by ryanhaigh on 2009-04-01
The easiest way to figure out what is going on is to use a disk usage analyser like Baobab. I'm pretty sure the gnome-utils package which contains this app comes with Ubuntu by default but not sure about Ultimate. Use this link to install it if its not already [apt://gnome-utils]("apt://gnome-utils"). You should then be able to find it in Applications>Accessories>Disk Usage Analyser.

Use Baobab to scan your home directory and determine where the largest files are. Its a stab in the dark as you say you are burning not creating this iso, but if you are in fact burning a movie in another format the image may have been created somewhere in your home.

---

### Post by sekinto on 2009-04-01
You can use the Disk Usage Analyzer (Applications > Accessories > Disk Usage Analyzer) to track down what is taking up all that space.

---

### Post by icarid_17 on 2009-04-02
this morning i started the computer, and now i've mysteriously got 9gb of space now, i know i deleted a few things, but they weren't very big, at any rate, i hope someone could help me figure out exactly what is going on here.

---

### Post by 3rdalbum on 2009-04-02
If you have your whole Ubuntu sitting in one partition, then you probably had a lot of gear in your /tmp directory. I imagine whatever burning software you were using was copying the ISO each time, although it shouldn't do that. It may have been something else sending data to /tmp. Since /tmp is the same partition as /home, it impacts on the amount of space available in your home directory.

That would explain why everything has gone back to normal now that you've rebooted - the contents of /tmp get deleted on startup.

---

### Post by icarid_17 on 2009-04-02
I do have my whole ubuntu installation on one partition, so you are probably right, i do wonder why burning causes info to be sent to tmp, but now at least i know why this is happening

---

### Post by 3rdalbum on 2009-04-02
Burning software generally creates an ISO from whatever files you are burning, and puts the ISO into /tmp. But if you're starting from an ISO, it doesn't need to put anything into /tmp.  So maybe your software has a bug.

---

### Post by icarid_17 on 2009-04-02
alright, i figure now that i at least have an idea of what may have happened I'll mark this thread solved, but to be honest, i can't figure out how

---

### Post by dcstar on 2009-04-02
> **sekinto said:**
> You can use the Disk Usage Analyzer (Applications > Accessories > Disk Usage Analyzer) to track down what is taking up all that space.

And using that utility from the menu will **not** show any files that are root only read permission.

If you want truly accurate information from that utility you have to launch it with:

```
gksudo baobab
```

---

### Post by icarid_17 on 2009-04-02
hello, i will try to use that, and assume that it was just something weird with the disc burning for now.

---

