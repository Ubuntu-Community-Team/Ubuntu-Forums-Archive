---
title: "How to Setup a Home-Server?"
date: 2006-08-29
forum: Desktop Environments
---

### Post by dedefbs on 2006-08-29
Hi there. I'm a ubuntu user for some time now, and i have two desktops(one with 32bit system and another with 64bit system)and i want ti setup a home-server here. I have Windows XP in the 32bits one and i made a server pretty easily with it, since it is really easy to setup it. However, i tried to do the same thing on the linux and i found myself into a damn trap. There is a how to do that on linux, but that's for gentoo(and it mostly uses iptables)](*,)  and since i'm a ubuntu user, i prefered to find faqs written by ubuntu users, but i haven't found a single article related to it on these forums. The how to that i found is pretty "manual configuration" for what i want. I know that the manual configuration is the best for security, but i really don't need that kind of security since is just my family that are using these pc's, so, I would really appreciate if there was another way to do it in ubuntu.
Ps:. That's the gentoo how to: [http://gentoo-wiki.com/HOWTO_setup_a_home-server#Introduction](http://gentoo-wiki.com/HOWTO_setup_a_home-server#Introduction)

If anyone wants to contact me, i have a blog:
[www.ospower.blogspot.com](www.ospower.blogspot.com)  
and you can reoply here as well that i will read it for sure!
Thanks guys!

---

### Post by kshymkiw on 2006-08-29
[http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper)

May have the information?  I didn't search, sorry

---

### Post by whizbaby on 2006-08-29
Hello!
Basically it is not difficult to share data over network in ubuntu, the problem is the closed-source behaviour of certain monopolists, making it hard to guess how their system works (that's why ntfs-write-support is still beta, that means your filesystem could get fubar if you use it). As far as I know
you should use SAMBA to share data with XP(ensive) servers, a collection of HOWTOS can be found here:

[http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/)

SAMBA also helps you to share devices like printers and scanners.
good luck!

---

