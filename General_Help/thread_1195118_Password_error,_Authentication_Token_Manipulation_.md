---
title: "Password error, Authentication Token Manipulation Error"
date: 2009-06-23
forum: General Help
---

### Post by supermario182 on 2009-06-23
I have Ubuntu 9.04 jj server installed and using it as a web server. Recently whenever I try to make a change that requires me to put in a password I click authenticate and the windows freezes and eventually has to be force quite (left it sitting for like 10 minutes once and it did nothing). I can still use sudo to do some things from command line, I can even use sudo su to get a root command prompt. However I cannot change the root password, or anyones for that matter, by using sudo passwd, or even going into sudo su and using passwd, it says "Authentication token manipulation error". Also when i log in, it says error after i type in the password but it still logs in, and when I use sudo it says error after i type the password but then continues to work as normal. Thanks for any ideas or suggestions.

---

### Post by supermario182 on 2009-06-29
hate to bump my own thread, but does anyone have an idea of what might be wrong here?

---

### Post by eiparrag on 2009-08-06
I got the same issue ... and still without a solution ...

---

### Post by Diamond2 on 2009-10-23
> **supermario182 said:**
> I have Ubuntu 9.04 jj server installed and using it as a web server. Recently whenever I try to make a change that requires me to put in a password I click authenticate and the windows freezes and eventually has to be force quite (left it sitting for like 10 minutes once and it did nothing). I can still use sudo to do some things from command line, I can even use sudo su to get a root command prompt. However I cannot change the root password, or anyones for that matter, by using sudo passwd, or even going into sudo su and using passwd, it says "Authentication token manipulation error". Also when i log in, it says error after i type in the password but it still logs in, and when I use sudo it says error after i type the password but then continues to work as normal. Thanks for any ideas or suggestions.

It's a likewise's bug
[https://bugs.launchpad.net/ubuntu/+source/likewise-open/+bug/302026](https://bugs.launchpad.net/ubuntu/+source/likewise-open/+bug/302026)

---

