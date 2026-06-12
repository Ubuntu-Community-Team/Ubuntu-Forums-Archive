---
title: "X Freezing"
date: 2006-06-06
forum: Desktop Environments
---

### Post by joker on 2006-06-06
Ok, I have been experiancing freeze ups (I believe just X) for quite some time now, It started when I upgraded from Hoary to Breezy. It happenes with both the upgrade and a fresh install, and with and without nvidia drivers.  I was hoping the issue would go away in Dapper but it is still happening.

The freezes happen mostly when web surfing, when a page is not responding (at least this is my guess). Once the operation times out or the data is recieved the computer un-freezes and works fine (until the next freeze anyway).  This happens with firefox and opera.  It has also happened when using other programs too, but rarely.  

Xorg.0.log and syslog don't show anything, I am not sure what other logs may be useful. 

If anyone can point me in a direction I would appreciate it.  

My hardware
Motherboard: Epox 8KHA, VIA KT266
video card: MSI G4Ti4400-VTD (Nvidia TI-4400)
Memory: 768mb DDR (I ran a 3 day memtest with no errors)

Also, the knoppix live CD doesn't seem to have any of these issues on this machine, I can surf all day with no probblems.  I can also use Windows without issue (Other than Ideological ;) ).  So I don't think it is hardware related.

---

### Post by _Doc_ on 2006-06-06
I had a problem with my geforce3 freezing on me... randomly it seemed... well what i did was i recompiled the kernel and removed nvidia frame buffer support and went with just generic frame buffer support.  This is in breezy.  

I believe in dapper you can blacklist this module and that way it won't load.  I don't remember what the module is called since i don't have it.  nvidiafb i believe is what it is called.  I think you can find the blacklist.d directory and black list it in there... that should help solve your problem... it solved mine :)

---

### Post by joker on 2006-06-08
The nvidiafb module (and lots of other frame buffer modules) is blacklisted by default in Dapper so that isn't it.  Any other ideas?

---

### Post by joker on 2006-06-09
If it helps, I was getting 2-3 second freezes while only downloading updates earlier tonight, definitely seems to be linked to net activity.

---

### Post by Installer36 on 2006-06-09
Joker , This may be way  off base but have you tried to disable the ipv6 in your web browser...I did this and it helped me with freezing during surf of the internet..type in the address bar about:config ....then in the filter box type ipv6 and then highlight to true....dont know why this works but it helps my internet surfing connection...Hope this helps ...Installer36

---

### Post by joker on 2006-06-09
I am going to try that, but I dobut that is the issue as the same thing happens when using apt or anything else that hits the net.  But I am willing to try anything at this point.

---

