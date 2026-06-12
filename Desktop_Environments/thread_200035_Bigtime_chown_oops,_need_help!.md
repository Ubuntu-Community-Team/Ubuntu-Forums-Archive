---
title: "Bigtime chown oops, need help!"
date: 2006-06-19
forum: Desktop Environments
---

### Post by elemental666 on 2006-06-19
so I was messing about with some external storage and my media libraries today.  I had to change the owner of all the files on an external drive that was mount just off my root dir.  So I went to the root dir and ran:
```
sudo chown -Rf myuser:mygroup mountpoint/ *
```

see that space between the mountpoint/ and the *

Yeah, I just changed the owner of EVERY FILE ON MY COMPUTER!!!

please tell me there is a way to recover from this?

---

### Post by shamrock_uk on 2006-06-19
[QUOTE=elemental666]so I was messing about with some external storage and my media libraries today.  I had to change the owner of all the files on an external drive that was mount just off my root dir.  So I went to the root dir and ran:
```
sudo chown -Rf myuser:mygroup mountpoint/ *
```

see that space between the mountpoint/ and the *

Yeah, I just changed the owner of EVERY FILE ON MY COMPUTER!!!

please tell me there is a way to recover from this?[/QUOTE]

Well, how about this:

```
sudo chown -Rf root:root /*
```

which should give root ownership of everything. 

Then ```
sudo chown -Rf myuser:mygroup /home/myuser/*
```

One thing I wouldn't do is restart for the moment! Whilst root belongs to every group, there may well be system files that are set to be read only by the owner and this may cause problems.

---

### Post by elemental666 on 2006-06-19
sudo is broken now as it belongs to my user and I don't have permission to change the owner even though it now belongs to me...

I'm just gonna restore a backup of the partition, which means the last 1.5hours of wrok are lost...

---

### Post by shamrock_uk on 2006-06-19
Disregard please

---

### Post by shamrock_uk on 2006-06-19
[QUOTE=elemental666]sudo is broken now as it belongs to my user and I don't have permission to change the owner even though it now belongs to me...

I'm just gonna restore a backup of the partition, which means the last 1.5hours of wrok are lost...[/QUOTE]

Hmm, well I've recreated this on mine and it does indeed look puzzling! 

Unfortunately suid cannot be used to gain privileges, only to lose them (which is great for security, just unlucky for you in this circumstance :))


I don't suppose you've enabled your root account previously? ( as this would make it very simple! ;))

Rather than restoring a backup, I would consider trying a live cd/ rescue cd - that should give you root privileges and I would imagine you could change the ownerships from there. 


I would be very interested to know the mechanics behind what is preventing us from changing the permissions on sudo, even when the file and folder are fully owned by us.

---

### Post by aysiu on 2006-06-19
Boot into recovery mode. That makes you root. Then you can chown anything you want.

---

### Post by elemental666 on 2006-06-19
thanks for your time and responses shamrock, they are appreciated.  I noticed that when I tried to do:

```
sudo chown root:root /*
```  I got error from sudo about setuid must be root, so then I tried:
```
chown root:root /*
```  Which of course resulted in a massive amount of permission errors.  I'm guessing this happened because I wasn't the root user, and even though I owned the files, certain segment of the file hierarchy can't even be touched by root, such as /proc and the like.  Also got lost of errors when trying to change owner in places like /user/sbin, /user/bin, etc etc.  Since I didn't have the root account setup (which I will do after the restore just in case...) I'm pretty much hosed.

I use partimage to make images of my partitions.  I run partimage from [SystemRescueCD]("http://www.sysresccd.org/Main_Page"), which is a live CD, that I highly recommend as its saved my bacon a couple of times already (not including this time ;) )

---

### Post by steve.horsley on 2006-06-19
Firstly, it may not be the whole system that got chowned - the * would have worked from the current directory wherever that was. 

Second, if everything has been chowned, I think restoring from a backup is probably a good idea. Not every file is supposed to be owned by root, and those oddballs are going to be hard to find and fix. To be honest, only 1.5 hours work lost is a very good score - your attention to backups is commendable.

---

### Post by shamrock_uk on 2006-06-19
[QUOTE=aysiu]Boot into recovery mode. That makes you root. Then you can chown anything you want.[/QUOTE]

When you get to the console, these are the commands you want:

```
cd /usr/bin/
chown root:root sudo
chmod 4777 sudo 
```

You may be able to tighten those permissions up from a security point of view later, but that will do the job. 

Hope it goes well ;)

---

### Post by elemental666 on 2006-06-19
[QUOTE=steve.horsley]Firstly, it may not be the whole system that got chowned - the * would have worked from the current directory wherever that was. [/QUOTE]

the -Rf is recursive and force...  I'm gonna drop the force from now on...

[QUOTE=steve.horsley]Second, if everything has been chowned, I think restoring from a backup is probably a good idea. Not every file is supposed to be owned by root, and those oddballs are going to be hard to find and fix. To be honest, only 1.5 hours work lost is a very good score - your attention to backups is commendable.[/QUOTE]

Well, after I crashed my brand new install about a million times, I figured out how to make images of my drives. I was kinda beginning to realize that there wasn't going to be a fix I could figure out and implement in a hour, so the backups saved the day.  Since I have /home and another directory on a different partition, I still had to fix a few straglers but I am back up and running now.  I've even got all the work I lost done now (always quicker the second time around eh).

Hell, I even learned something new :)

Thanks again.

---

