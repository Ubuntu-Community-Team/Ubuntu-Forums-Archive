---
title: "Odd Thunderbird behaviour"
date: 2006-09-07
forum: Desktop Environments
---

### Post by s1mple_M4N on 2006-09-07
Hi all - not sure if this is the right forum to post in, but after searching and finding nothing to help me with this problem, here goes.

I just reinstalled Dapper 6.06 LTS (dual-boot with XP Home) and after doing system updates installed and ran Automatix.

I prefer Thunderbird email to any other client, so installed that then ran in Terminal "sudo mozilla-thunderbird -profilemanager" to load my user profile from a shared folder on my home network file server.

Strangely, each time i start Thunderbird now it asks me to create a profile. So I point it in the right direction, click start thunderbird and everything is OK. I have even copied my profile folder to this machine but still I am asked to create a profile every time Thunderbird starts.

Any ideas??

Any help appreciated,

RoyJ

---

### Post by s1mple_M4N on 2006-09-07
D'OH!

It would seem, that by using 'sudo' when I created the original profile, I locked the .mozilla-thunderbird folder in my home folder to root rather than myself.

I found another post about editing profiles.ini in that folder and when I browsed to it it was locked.

Thanks to anyone who has looked at my previous post and thought about responding - problem is now solved.

Every Linux day is a learning day :-D

---

