---
title: "downloading slower in linux?"
date: 2006-08-31
forum: Desktop Environments
---

### Post by homy06 on 2006-08-31
I was wondering why my download rate is slower in linux than when I was using XP?

I mean in torrents mainly. is it bc of a firewall issue? I tried adding my bit torrent port to firestarter but it makes it slower. so is there a way to make torrents faster in linux? 

and if no one wants to answer the above (please do) I was wondering this. 

My firefox homepage is set to gmail, but every time it starts it starts at arizona.edu. does this mean that i have a virus? I mean, I changed it under preferences, yet it somehow bypasses it. i ran f-prot and it found nothing. 

Another problem is Tribler around the same time started crashing, as soon as i clicked within the window it would close. I unistalled it and reinstalled it, and it somehow remembered the torrent in its task file, even though I erased the task, does this mean ubuntu like windows doesn't properly erase stuff off the drive?

PLEASE ANSWER some of the question if you can pleaaaaaase

---

### Post by aysiu on 2006-09-01
> **homy06 said:**
> 
My firefox homepage is set to gmail, but every time it starts it starts at arizona.edu. does this mean that i have a virus? I mean, I changed it under preferences, yet it somehow bypasses it. i ran f-prot and it found nothing. Go to System > Preferences > Preferred Applications. If you see ```
firefox %u
``` or ```
firefox %s
``` change it to ```
firefox
```

---

### Post by homy06 on 2006-09-01
and what if it doesn't allow me to delete it? Like i even tried highlight and then right click delete, and nothin?
thanks

---

### Post by homy06 on 2006-09-01
nevermind, i made sure the drop down box was set to custom


thank you, i will name my first born aiysu.

could anyone else help?

---

### Post by codejunkie on 2006-09-01
> **homy06 said:**
> I was wondering why my download rate is slower in linux than when I was using XP?

I mean in torrents mainly. is it bc of a firewall issue? I tried adding my bit torrent port to firestarter but it makes it slower. so is there a way to make torrents faster in linux? 

and if no one wants to answer the above (please do) I was wondering this. 

My firefox homepage is set to gmail, but every time it starts it starts at arizona.edu. does this mean that i have a virus? I mean, I changed it under preferences, yet it somehow bypasses it. i ran f-prot and it found nothing. 

Another problem is Tribler around the same time started crashing, as soon as i clicked within the window it would close. I unistalled it and reinstalled it, and it somehow remembered the torrent in its task file, even though I erased the task, does this mean ubuntu like windows doesn't properly erase stuff off the drive?

PLEASE ANSWER some of the question if you can pleaaaaaase

it's because windows is specifically optimized for downloading via p2p networks, gates and balmer insisted on this because they love to download bootleg anime and brittneys latest hits through kazaa. :D just kidding seriously though it could be **ipv6** with some routers and even some isp's like mine, the overall connection speed is slower when ipv6 is enabled. open a terminal and enter this command ```
ip a | grep inet6
```if something like this shows up 
```

[root@localhost ~]# ip a | grep inet6
    inet6 ::1/128 scope host
    inet6 fe80::216:ecff:fe1d:c4d8/64 scope link
[root@localhost ~]#

```
you need to disable ipv6, here's a link that will help you with disabling ipv6 that should increase the speed quite a bit.
[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

---

### Post by homy06 on 2006-09-01
thank you codejunkie, it worked!
although, you're name isn't cool enough to be named after any new borns, I'll make sure its the middle name.

---

### Post by codejunkie on 2006-09-01
> **homy06 said:**
> thank you codejunkie, it worked!
although, you're name isn't cool enough to be named after any new borns, I'll make sure its the middle name.
glad you got it working and i thank god that your not going to name that child after me, having a name like codejunkie surly wouldn't be any fun on that child :wink:.

---

