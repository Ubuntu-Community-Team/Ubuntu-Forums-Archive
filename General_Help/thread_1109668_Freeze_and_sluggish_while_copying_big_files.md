---
title: "Freeze and sluggish while copying big files"
date: 2009-03-29
forum: General Help
---

### Post by afeasfaerw23231233 on 2009-03-29
In Ubuntu the system freezes and becomes extremely sluggish when it is copying big files, say 20GB. It happens on both my desktop and notebook computer. In Windows XP although the speed is a bit slower the performance and responsiveness is still very acceptable. In Ubuntu I can't simply do anything except waiting the copying process to finish. 

I googled around and couldn't get much results. 

Any body came across the same problem?

EDIT: The cpu usage is never high (<10%) while copying big files. The copying speed is not slow but the whole system is.

EDIT2: Although gkrellm shows the cpu usage is <10%, by the top command %wa is 95% and %id is 0%. The man page says "%wa" is an indication of the amount of CPU time wasted while waiting on I/O operations to complete. 
What should I do?

---

### Post by dcstar on 2009-03-29
> **afeasfaerw23231233 said:**
> In Ubuntu the system freezes and becomes extremely sluggish when it is copying big files, say 20GB. It happens on both my desktop and notebook computer. In Windows XP although the speed is a bit slower the performance and responsiveness is still very acceptable. In Ubuntu I can't simply do anything except waiting the copying process to finish. 

I googled around and couldn't get much results. 

Any body came across the same problem?

There have been many posts like this, I don't have too many problems on my 8.04 64-bit system but I have it optimised to reduce unnecessary disk overhead.

Adding these options to all your /etc/fstab ext3 lines should improve things as it reduces unnecessary directory writes:

```
UUID=whatever / ext3 relatime,errors=remount-ro,**nodiratime,noatime** 0 1
```

---

### Post by afeasfaerw23231233 on 2009-04-01
Thanks for your reply. 
I've just tried your suggestion. Still sluggish. Doesn't notice any difference.

---

### Post by afeasfaerw23231233 on 2009-04-01
EDIT: The cpu usage is never high (<10%) while copying big files. The copying speed is not slow but the whole system is.

EDIT2: Although gkrellm shows the cpu usage is <10%, by the top command %wa is 95% and %id is 0%. The man page says "%wa" is an indication of the amount of CPU time wasted while waiting on I/O operations to complete. 
What should I do?

---

### Post by afeasfaerw23231233 on 2009-04-02
bump

---

### Post by philinux on 2009-04-02
I find nautilus slow when copying lots or large files but using the cp command is usually very quick.

---

### Post by afeasfaerw23231233 on 2009-04-02
But my problem is not "slow copying speed". The copying speed isn't slow. But while copying large files it nearly freezes my computer. The whole system becomes unresponsive, for example, open a terminal takes two minutes. I can do nothing except waiting the copying process to finish. 
In XP the system is only "less responsive" and still usable. I can use any other application while copying big files, though the speed is slower.

---

### Post by afeasfaerw23231233 on 2009-04-11
bump

---

### Post by dcstar on 2009-04-11
> **afeasfaerw23231233 said:**
> But my problem is not "slow copying speed". The copying speed isn't slow. But while copying large files it nearly freezes my computer. The whole system becomes unresponsive, for example, open a terminal takes two minutes. I can do nothing except waiting the copying process to finish. 
In XP the system is only "less responsive" and still usable. I can use any other application while copying big files, though the speed is slower.

I can't remember when CFQ was made the default in the Ubuntu kernels, but you might try this to experiment with different options:

[http://ubuntuforums.org/showthread.php?t=119546](http://ubuntuforums.org/showthread.php?t=119546)

---

### Post by afeasfaerw23231233 on 2009-04-11
Thanks for your suggestion. I added "elevator=cfq" to the kernel line but cannot notice any difference.

```
 kernel          /vmlinuz-2.6.24-22-generic root=UUID=f4659fbf-000d-49b8-9934-99a69ffec0e1 ro quiet elevator=cfq 
```

---

### Post by afeasfaerw23231233 on 2009-04-18
bump. no one has this annoying problem?

---

### Post by afeasfaerw23231233 on 2009-04-25
Bump

---

### Post by MellonCollie on 2009-04-25
> **afeasfaerw23231233 said:**
> no one has this annoying problem?


I do, but nowhere near as bad as you described. I notice a sluggishness in the UI when shifting a large amount of data around. I've always put it down to the way the kernel handles disk I/O, because I don't experience it in Vista/7.

---

### Post by arashiko28 on 2009-04-25
I think it could be your RAM, have you checked it? If you're consuming too much it'll be obvious, try to copy something big with you system monitor on screen, there you can have an idea of what's going on.

Other thing is if you use Ekiga. I had this problem once with it, comes to be that if you open Ekiga and then shut it, there's this application, bonobo that stays up and eats up your CPU usage, It had me overclocking for about a week until I realized about it. No matter if you restart, the damn thing kept coming back, my solution was to uninstall Ekiga.

---

### Post by afeasfaerw23231233 on 2009-04-27
Thanks for your suggestion. I have gkrellm monitoring my system all the time. Definitely it is not a RAM problem.

---

### Post by Alexander Lindskog on 2009-05-04
I too share your problem. 

During a backup i copied 500gig from one physical disk to another and experienced the sluggish-ness you described. Also not a RAM-problem.

As far as i understand reading and writing large files quickly flushes the cache of your previously used programs forcing the system to load them from disk every time. With the added load of copying files this makes the process painstakingly slow.

If you were able to exclude your copy process from using the disk cache this wouldn't be a problem but I've yet to find a simple way to do this.

They discuss some hack to avoid caching here:
[http://ubuntuforums.org/showthread.php?t=489719](http://ubuntuforums.org/showthread.php?t=489719)


Regards, 

Alex

---

