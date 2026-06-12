---
title: "Slow gnome startup, which process I\O bound?"
date: 2008-12-30
forum: General Help
---

### Post by Cenoforums on 2008-12-30
Hi,

I'm running ubuntu on an acer aspire one. It runs slow mainly because of the internal flash disk being itself extremely slow.
One of the worst issues is gnome itself is taking something close to 20seconds to fully initilize because some process is completely hogging the disk. 

I am sure this is the case because I can run top before said process begins accessing the disk and can see that nothing is happening on the cpu side. CPU usage runs somewhere close to 20%. Yet clicking the main gnome menu takes forever because of the time it takes to load the icons from the disk.

Is there any program I can run that will monitor which process is acessing the disk? I know that strace can log all the system calls done by a process, but that was the only thing I could find on the subject.
Bootchart stops logging stuff as soon as gnome starts. Maybe it has an option I'm not aware of?

My plan is to find out which process is slowing the gnome boot and see if I can take it out from the start up list.

Thanx
Ceno

---

### Post by redilyn on 2008-12-30
While I do not have an answer to your question I would suggest checking out eeebuntu base.

It is a very basic install without all the bells and whistles. Might be just what you need.

---

### Post by sdennie on 2008-12-30
Yes but, it will probably drown you with information and may not be very useful in this case.  Before logging into gnome, hit Ctl-Alt-F1, login and then do:

```

sudo sh -c "echo 1 > /proc/sys/vm/block_dump"

```

Now hit Ctl-Alt-F7 and login as normal.  Once you are logged, look at the bottom of /var/log/syslog and you should see what was using your disk during login.  Again, this might be too much information to parse properly.  To turn off that log spam use:  

```

sudo sh -c "echo 0 > /proc/sys/vm/block_dump"

``` 

Most of the boot process is I/O bound because none of the relevant data is sitting in the disk cache yet.  One possible solution to this would be to use preload:

```

sudo apt-get install preload

```

That should allow for the login to happen faster because as you are typing in your username/password, the preload daemon should be priming your disk cache.  It does take preload some time to become "smart" so, you may not immediately notice this change.  How much faster it will make the login process probably depends on how quickly you can type in your username and password.  ;)

---

### Post by Cenoforums on 2008-12-30
vor, thanks a lot for the input.

I was able to put block_dump to 1. As described here [http://www.linuxinsight.com/proc_sys_vm_block_dump.html](http://www.linuxinsight.com/proc_sys_vm_block_dump.html) , without any modification just setting the flag to 1 will be intrusive to the whole process. But still, I made a small script and was able to put the flag to 1 and then watch it live by tailing /var/log/syslog.

I think that sadly the behavior I'm experiencing is normal, or consequence of default settings. The process that consumes I\O the most is pdflush, that from a quick google I'm getting is related to flushing the cache to disk. Gnome-settings-log also does some stuff.

I really don't understand enough of operating systems do put forth an optimization. Ideally, if whatever the hell pdflush is doing could be set to be spread out to a longer time, then I wouldn't experience hanging. Do you think I can control this? I think the file laptop_mode is related to this, but honestly I don't really understand it.

---

### Post by sdennie on 2008-12-30
You can control pdflush and, for ext3, the journal commit time.  I wrote a guide about it here: [  HOWTO: Decrease disk activity]("http://ubuntuforums.org/showthread.php?t=839998").  But, I think setting them to higher values probably won't help in your case.  Another possible place to look for help is here: [http://ubuntuforums.org/showthread.php?t=565651](http://ubuntuforums.org/showthread.php?t=565651).  This solution is in many ways similar but slightly more involved than the preload solution I mentioned in my last post.

---

### Post by Cenoforums on 2008-12-30
the preload thing is useless in my case because I have the automatic login thing activated. I already use ext2 instead of ext3 because of the journalling feature.

Tomorrow I will try the readahead solution, though it's more than just "slightly" involved lol. Tomorrow because I need some background on readahead since I have never tried it.

But since I'm writing this, do you think it's plausible to use readahead if my netbook only has 512mb ram?

---

### Post by sdennie on 2008-12-30
> **Cenoforums said:**
> 
But since I'm writing this, do you think it's plausible to use readahead if my netbook only has 512mb ram?

It may not benefit you with 512M of RAM but I actually don't know.  I think if you have a slow disk and very little RAM, you may unfortunately have to accept that your machine is not going to be blazingly fast.  I'm actually a bit surprised that startup time is an issue if you have the ability to use suspend/resume though.  With that, startup time should be like 5 seconds and has the added benefit of leaving your applications open.

---

