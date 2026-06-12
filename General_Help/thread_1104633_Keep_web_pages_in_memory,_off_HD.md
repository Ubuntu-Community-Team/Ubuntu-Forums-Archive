---
title: "Keep web pages in memory, off HD?"
date: 2009-03-23
forum: General Help
---

### Post by ToFue on 2009-03-23
Hi, I'm wondering at how to float web pages in memory, instead of letting them clutter my hard drive as I browse.. My /home partition isn't *that* big (rest of disks are used for audio/ video editing and storing dvd backups), and I think that'll let me archive larger files instead of getting surprised that I'm out of space.. :p

Can anyone educate me in the direction I need to research?

Thanks!

---

### Post by Xiong Chiamiov on 2009-03-23
What exactly are you trying to do?  Are you concerned with the size of the cache from your browser?

---

### Post by ToFue on 2009-03-23
> **Xiong Chiamiov said:**
> What exactly are you trying to do?  Are you concerned with the size of the cache from your browser?

not necessarily.. I was moreso thinking of the live cd, and thought about advantages that could be had for not printing every visited page and object onto the HD.. that the cache would remain in ram only and not even make it to the hard drive ;)

i.e.: when (just a matter of time & tinkering) my sys goes down again, I won't have to sort through ALL 100+ folders of web page material just to find my jems when I use photorec or other file recovery

---

### Post by ToFue on 2009-03-24
bump..

---

### Post by FluffyElmo on 2009-03-24
Can't you just reduce your browser cache? I'm on OS X at the moment so I can't check, but just set your cache to 0 mb in the preferences and it should accomplish what you want.

---

### Post by ToFue on 2009-03-24
oh excellent.. it's the simple solutions that are usually overlooked!

---

### Post by zika on 2009-03-24
or put Your cache directory in /dev/shm [http://ubuntuforums.org/showpost.php?p=6705815&postcount=23](http://ubuntuforums.org/showpost.php?p=6705815&postcount=23) or in /tmp that is mounted as tmpfs (... []("http://ubuntuforums.org/showpost.php?p=6705815&postcount=23")add a line in /etc/fstab```
tmpfs /tmp tmpfs defaults 0 0
```and make browser put its cache in /tmp).

---

### Post by Slim Odds on 2009-03-24
> **zika said:**
> or put Your cache directory in /dev/shm [http://ubuntuforums.org/showpost.php?p=6705815&postcount=23](http://ubuntuforums.org/showpost.php?p=6705815&postcount=23) or in /tmp that is mounted as tmpfs (... add a line in /etc/fstab```
tmpfs /tmp tmpfs defaults 0 0
```and make browser put its cache in /tmp).

I've seen this before and it makes no sense.

Your browser maintains two caches, one in memory and one on disk. So just disable the disk cache. Putting the disk cache in memory is redundant and useless.

---

### Post by zika on 2009-03-24
> **Slim Odds said:**
> I've seen this before and it makes no sense.
Your browser maintains two caches, one in memory and one on disk. So just disable the disk cache. Putting the disk cache in memory is redundant and useless.
it is Your opinion and I honor it.
I did not say that I push this as a solution for ...(whatever)... I've tried it and it works if You have some memory just lying around unused. maybe You should try it ... I just answered to the question given as a title of the thread: **Keep web pages in memory, off HD?**
...
[I]OP:I'm wondering at how to float web pages in memory, instead of letting them clutter my hard drive as I browse.. 
OP:that the cache would remain in ram only and not even make it to the hard drive [/I]
...
rotating cube in front of me while I try to work makes no sense to me but I never attacked anybody who wants to do that. I helped some of them with graphics problems in order that they become able to do that.

---

### Post by Slim Odds on 2009-03-24
> **zika said:**
> rotating cube in front of me while I try to work makes no sense to me but I never attacked anybody who wants to do that. I helped some of them with graphics problems in order that they become able to do that.

I'm sorry that you feel like there was an attack (as there was none).

Just disable the disk cache and let it use memory. That's all I'm saying.

---

### Post by zika on 2009-03-24
> **Slim Odds said:**
> I'm sorry that you feel like there was an attack (as there was none).
Just disable the disk cache and let it use memory. That's all I'm saying.
I might have used a wrong word. no hard feelings on my side. in my experience not all the stuff would be held in memory during the working day and I suggested a thing that worked for me for some time. if it have wanted to stay in memory without that "tweak" I would have not used it, believe me, since I'm minimalist in the core. I have not got to that after installing 9.04 and got entangled in some other stuff like 2.6.29 e.t.c. beside the main work ... glad this has reminded me ... :)

it took me a while to remember all pros and cons: one thing that is a good advocate for my side is: once You close the browser all the cache from memory is gone. if it is in tmpfs it is there until You reboot. since tmpfs is of limited size it is not a danger for Your other applications. only caveat is the case when You want do to DL or work with big files and in that case that limitation on the size of /tmp can make problems ...

---

### Post by Slim Odds on 2009-03-24
> **zika said:**
> it took me a while to remember all pros and cons: one thing that is a good advocate for my side is: once You close the browser all the cache from memory is gone. if it is in tmpfs it is there until You reboot. since tmpfs is of limited size it is not a danger for Your other applications. only caveat is the case when You want do to DL or work with big files and in that case that limitation on the size of /tmp can make problems ...

Good points... thanks for the additional thoughts...

---

### Post by kerry_s on 2009-03-24
i agree with everyone else, firefox just needs tweaking.

my thoughts:
reduce the cache don't disable it. mine is 5mb instead of the normal 50mb. mine see pic.

other thoughts:
change the way memory is used on your system.

/etc/sysctl.conf

```
vm.overcommit_memory = 1
vm.overcommit_ratio = 95
vm.dirty_ratio = 5
vm.swappiness = 1

```

---

