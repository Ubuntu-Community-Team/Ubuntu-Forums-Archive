---
title: "Some doubts about ubuntu"
date: 2009-05-10
forum: General Help
---

### Post by Scrilax on 2009-05-10
Hi, I'm a newbie in ubuntu but I am already familiarized with some some linux distros (not too much), The "ubuntu" account from the live cd is the root, it appears so. I created a new account but everytime I want to do some that needs root permission I can't do it (I Don't Know the root password =/ neither can change it with the passwd command).. Can someone help me with this ?

Another question, is possible to be "attacked" I mean, the live version that I have, without any firewall and other kind of defense programs.. can someone spy on me ? or get access remote to my computer ?

Thanks in advance :)

---

### Post by mike555 on 2009-05-10
Ubuntu doesn't have a "root" account (unless you make one) ,it uses super user commands in terminal , so if you wanted to use nautilus as root you could type "  sudo nautilus  " in terminal ....... you can't really install anything when using the live cd , because as soon as you shut down it's gone .....
    the live cd is kinda more for testing your system to be sure it's hardware will work , or for repairs , or getting data off a broken operating system ....

---

### Post by kaibob on 2009-05-10
The following is an excellent discussion of root and sudo in Ubuntu:

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by spiderbatdad on 2009-05-10
> can someone spy on me ? or get access remote to my computer ?
 The short answer is...Yes. Always.

---

### Post by Scrilax on 2009-05-10
thanks for the help, but refering to the security issue, how could I get rid of it ?

---

### Post by spiderbatdad on 2009-05-10
lol...the only sure way is unplug your computer...as the saying goes.
surely you realize your isp sees all traffic, not to mention a zoo of snooping tools available to those who would exploit any vulnerabilties found in your internet traffic. You could spend a life time trying to be totally anonnymous on the internet, idk if you could succeed.

---

### Post by CatKiller on 2009-05-10
> **Scrilax said:**
> Another question, is possible to be "attacked" I mean, the live version that I have, without any firewall and other kind of defense programs.. can someone spy on me ? or get access remote to my computer ?

The live cd environment doesn't have any services running; no web server, no mail, no ssh. There's nothing for any attacker to connect to. And even if they could connect, all they would see is the same live environment that they could get by downloading and running the ISO themselves. It's not like you're saving all your highly sensitive personal information there; it's a live cd environment. You can't write anything permanent there. As soon as you reboot your computer, it's all gone.

All of the information that you send over the wild Internet is interceptable. Whatever environment you're in. You're entrusting it to your ISP and all the ISPs between you and the packet's destination, and entrusting that the destination hasn't been compromised. A number of ISPs have been happy to pass your packets to third parties so that they can either advertise at you or monitor your activities against their pattern-matching algorithms. People will always be able to spy on you.

As spiderbatdad says, the only way to mitigate against this completely is to disconnect yourself from the Internet and never go out or talk to anyone. Otherwise, you're going to have to accept some level of risk.

---

