---
title: "Strange networking problem.  Nothing but google :-("
date: 2009-05-30
forum: General Help
---

### Post by bbabu84 on 2009-05-30
I installed Ubuntu 9.04 (desktop) on my system (motherboard by Shuttle).  When I use the new system, the browser is unable to go to web sites that are not *.google.com.  Yes, it sounds strange.  I can go to any of google's sites (maps, mail, etc), but if I try to go to ubuntuforums.org or yahoo.com, it just waits indefinitely.  The networking connection and DNS seem ok, since I can open a terminal and use ssh to log into other boxes outside my LAN.  I also used apt-get from a terminal and that also seems to work.

Here is an older discussion that raised a similar issue:
[http://ubuntuforums.org/archive/index.php/t-579900.html](http://ubuntuforums.org/archive/index.php/t-579900.html)

I tried Ubuntu 8.10 and Fedora 10 on the same box, and they all have the same problem.  Does any one know why this problem is occurring and what the solution is?  Any help is appreciated.  Thanks.

BB

---

### Post by mrog on 2009-05-30
Perhaps it's a google conspiracy?

Other than that, if you type "dig yahoo.com" in a terminal, do you get an appropriate response? (there are three IP addresses)

And, are you able to get to your ISPs website? If you can, the issue is likely with your ISP and/or you might need to go to a specific page on their site so they can get your MAC address. Some ISPs will not provide DNS results until you do this or fix this issue with them. Try just going to their site and then somewhere-else first before you spend too much time on this.

This is the only possibility I can think of. I'd imagine they let you get to google so you can find them.

---

### Post by albinootje on 2009-05-30
> **bbabu84 said:**
> When I use the new system, the browser is unable to go to web sites that are not *.google.com. 

Can you try with the OpenDNS DNS servers ?
[https://www.opendns.com/start/device/ubuntu](https://www.opendns.com/start/device/ubuntu)

---

### Post by lswb on 2009-05-30
This thread mentions another possible problem if the networking details are similar to yours:

[http://ubuntuforums.org/showthread.php?t=855691&highlight=mtu](http://ubuntuforums.org/showthread.php?t=855691&highlight=mtu)

Check at message #8

---

### Post by bbabu84 on 2009-06-01
Thanks to mrog, albinootje, lswb for the responses.  I changed the mtu to 1400 as suggested by one of the responses in the link posted by lswb, and the problem has vanished.  I have not tried to optimize the value of mtu.  I am just happy that the problem is solved.  Thanks again.

BB

---

