---
title: "Test Driving Ubuntu"
date: 2006-07-03
forum: Desktop Environments
---

### Post by darkwoofe on 2006-07-03
I just installed ubuntu as a dual boot on my PC. The install was quick, and with the exception of the nerve wracking (First Time Ever) partitioning of my hard drive (Got it right in one try) very easy. I tried the live CD and loved it, so I plan to try it out for real and if l like it as much as I think I will, I'll switch completely from Windows XP.

Now that it's installed, I wanted to ask if anyone can recommend any firewall and anti-virus software? 
Also, if there's anything important that I may have missed that you think I should know? Maybe some fun facts or downloads?

---

### Post by Jagot on 2006-07-03
Firestarter is probably the most popular firewall config program available - it is available in the universe repo.  To enable it, along with the multiverse repo, look here:

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

One of the first things I do is to add support for restricted formats and Java - you can find out about it here:

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

You may want to have a look through this to start you off:

[https://help.ubuntu.com/ubuntu/desktopguide/C/index.html](https://help.ubuntu.com/ubuntu/desktopguide/C/index.html)

This is also pretty good also:

[http://easylinux.info/wiki/Ubuntu_dapper](http://easylinux.info/wiki/Ubuntu_dapper)

---

### Post by ardchoille on 2006-07-03
[QUOTE=darkwoofe]I just installed ubuntu as a dual boot on my PC. The install was quick, and with the exception of the nerve wracking (First Time Ever) partitioning of my hard drive (Got it right in one try) very easy. I tried the live CD and loved it, so I plan to try it out for real and if l like it as much as I think I will, I'll switch completely from Windows XP.

Now that it's installed, I wanted to ask if anyone can recommend any firewall and anti-virus software? 
Also, if there's anything important that I may have missed that you think I should know? Maybe some fun facts or downloads?[/QUOTE]

I have been using Linux for more than 5 years and haven't seen the need for anti-virus software - I threw Windows away back in 2000 and haven't used it since. Face it, with the way Linux is set up (normal users don't run as root), writing viruses for Linux just doesn't do the amount of damage on Linux that viruses do on Windows operating system.. so writing a virus for Linux is kind of a waste of time. Without root permissions, a virus just can't do much damage to a Linux system.

I do, however, recommend a rootkit checker as rootkits **CAN** do a good amount of damage on Linux systems. Two good rootkit checkers are chkrootkit and rkhunter, both are in the Ubuntu repos.

---

### Post by darkwoofe on 2006-07-03
Thanks everyone! This helps a lot. I didn't think I'd get the hang of a new OS so quick, but it's not hard all. Add in the great help/support I've gotten from this forum and things have been a breeze.

---

