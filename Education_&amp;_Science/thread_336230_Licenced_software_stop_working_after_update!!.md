---
title: "Licenced software stop working after update!!"
date: 2007-01-11
forum: Education &amp; Science
---

### Post by dsokus on 2007-01-11
Hi,

I had functional and properly licenced (purchased!) Mathematica and Maple installations on my computer, running Kubuntu Dapper. After a certain update (or something), my "HostID"'s in both applications have changed. I have NOT upgraded to Edgy, the computer is still running Dapper. 

I got around the problem in Mathematica by actually emailing the company and asking for another password to help me.. However, Maple reports "Missing host ID for licence server", which is something of a problem as I don't even know what to do with it!! 

Anybody having the same problem? Why does it happen - it's a very annoying thing, can it somehow be avoided - makes me want not to update my computer... And how can I solve it? 

Thanks
Zsuzsi

---

### Post by neoflight on 2007-01-11
> **dsokus said:**
> Hi,

I had functional and properly licenced (purchased!) Mathematica and Maple installations on my computer, running Kubuntu Dapper. After a certain update (or something), my "HostID"'s in both applications have changed. I have NOT upgraded to Edgy, the computer is still running Dapper. 

I got around the problem in Mathematica by actually emailing the company and asking for another password to help me.. However, Maple reports "Missing host ID for licence server", which is something of a problem as I don't even know what to do with it!! 

Anybody having the same problem? Why does it happen - it's a very annoying thing, can it somehow be avoided - makes me want not to update my computer... And how can I solve it? 

Thanks
Zsuzsi

post the contents of /etc/host**s** file? xxxxx 'fy the username ofcourse!

---

### Post by dsokus on 2007-01-11
127.0.0.1 localhost zsuzsi-laptop
127.0.1.1 zsuzsi-laptop

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


'fy? :confused:

---

### Post by neoflight on 2007-01-12
> **dsokus said:**
> 127.0.0.1 localhost zsuzsi-laptop
127.0.1.1 zsuzsi-laptop

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


'fy? :confused:

hmm...did u change any script file to make maple of mathematica executables? may be check those?

---

### Post by dsokus on 2007-01-12
No I don't remember changing anything - I just ran the installers as normal.

---

### Post by Hendrixski on 2007-01-12
Wow, when did Mathematica start shipping for Linux.  That's cool!

---

### Post by neoflight on 2007-01-12
did u try to install maple again after the update? any installation error? 
here is an [error report]("http://www.mapleprimes.com/forum/maple-10-64-bit-installation-problems") for 64b.

[this]("http://www.maplesoft.com/support/faqs/FLEXlm/1.aspx") might also help

---

### Post by mkw87 on 2007-01-12
See if you can find the license file in the installation folder.  If you can find that you can probably edit the name of the host to match that of your computer - this COULD solve the problem (it should).  Be sure to back it up before editing it.

---

### Post by kullan&#305;c&#305; on 2007-01-12
Not that I know of. OpenOffice is also horrible about knowing lit crit/social sciences terms. I think, though, that if you're inclined you can save all the science terms you've had to add to a new dictionary, export it, and make it available for others to use.
look:
[www.unreadedpost.com](www.unreadedpost.com)

---

### Post by icefaerie on 2007-01-15
I've experienced this problem.  I find that if you just use the kernel you were using when you originally installed Mathematica, it works fine.  Oddly, I've experienced this on some machines and not others.  I don't really know why it does that...

---

