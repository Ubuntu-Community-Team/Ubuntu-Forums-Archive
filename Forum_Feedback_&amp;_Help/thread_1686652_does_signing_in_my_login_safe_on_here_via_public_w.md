---
title: "does signing in my login safe on here via public wi-fi?"
date: 2011-02-12
forum: Forum Feedback &amp; Help
---

### Post by shiningkenmonster on 2011-02-12
hello. i use a linux netbook on the go everywhere. the main source of the my internet connect is public wifi. 

Does this forum already encrypts my login info?
i have already type in the extra "s" to enable SSL. which is:
[https://www.ubuntuforums.org/](https://www.ubuntuforums.org/)

but it doesn't let me access the website.

i have tried using the sign on with Launchpad account too. but it says i need to enter my ubuntu username and password everytime. thus still using "http:" without the extra "s".

can a staff member tell me if this forum already encrypt my login info? or do i need another step?

btw, i can't install any applications. or compile by source yet. I have the Google Chrome OS on the CR-48. which the OS is built on top of Ubuntu but the terminal is very limited.

I don't have a server at home. no internet at home, so i can't ssh into a vpn tunnel.

---

### Post by movieman on 2011-02-12
SSL is secure even over insecure links. However, cookies are sent in the clear if you use http: to connect to the site after logging in, so they can be stolen and used to pretend to be you for the duration of that session.

As such, ideally you should run the entire session through SSL to keep the cookies encrypted too, or at least log out after you're done so the cookies will no longer be valid if someone did steal them.

---

### Post by tjwoosta on 2011-02-13
Duplicate thread

[http://ubuntuforums.org/showthread.php?t=1686272](http://ubuntuforums.org/showthread.php?t=1686272)

---

### Post by cascade9 on 2011-02-13
IIRC you can login using launchpad. 

> **shiningkenmonster said:**
> btw, i can't install any applications. or compile by source yet. I have the Google Chrome OS on the CR-48. which the OS is built on top of Ubuntu but the terminal is very limited. 

chromeOS is not made so you can install programs. Google want people to do everything online with chromeOS, so that they can collect data about you and sell it. ;) 

It might be 'built on ubuntu' and use the linux kernel, but thats about all its got in common with normal linux distros.

---

