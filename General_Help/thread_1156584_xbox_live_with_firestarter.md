---
title: "xbox live with firestarter"
date: 2009-05-11
forum: General Help
---

### Post by dr.pepper23 on 2009-05-11
I'm trying to connect to xbox live through ubuntu. I could do it in vista just fine, but I don't want to have to move over to vista just to get on live. I've got my xbox plugged into a laptop, which is connected to the internet wirelessly. I'm trying to do it with firestarter, so I've got my firestarter connected through wlan0, which is my internet connection, and eth0, which is the xbox connection. Only problem is i get "The device eth0 is not ready" when I try to start firestarter. Any suggestions?

---

### Post by max_power on 2009-05-11
could you please explain step by step how you are connecting your xbox to your computer?

both devices should be hooked up to a router which is connected to the internet.

---

### Post by dr.pepper23 on 2009-05-11
I've just got a crossover cable running from my xbox to my computer. The computer is connected to the internet wirelessly. I don't think they both have to be hooked up to a router because I have done this successfully with the same setup in vista. I just don't know how to get it to work in ubuntu.

---

### Post by max_power on 2009-05-12
hmmm... what application were you using in Vista to interface with your xbox? Or does Vista recognize the Xbox name automatically? if so, then you probably wont get the same type of operation in Linux.

---

### Post by prem1er on 2009-05-12
NVM: didn't read your post correctly, sorry.

---

### Post by dr.pepper23 on 2009-05-12
> **max_power said:**
> hmmm... what application were you using in Vista to interface with your xbox? Or does Vista recognize the Xbox name automatically? if so, then you probably wont get the same type of operation in Linux.

Vista recognizes it automatically. I've read around and people say that it can be done with firestarter, but I get the error message "Device eth0 is not ready?" They also say it can be done with iptables, but I didn't really want to mess around with that. Figured it would be easier with firestarter.

---

### Post by max_power on 2009-05-12
firestarter is just a firewall. [http://en.wikipedia.org/wiki/Firewall_(networking)]("http://en.wikipedia.org/wiki/Firewall_(networking)")

---

### Post by dr.pepper23 on 2009-05-12
Yea I know. But from what I've read other people have been able to use firestarter to solve my problem. The firestarter website says it enables internet connection sharing, as well as other stuff. 

[http://www.fs-security.com/ ]("http://www.fs-security.com/")

Isn't that what I want?

---

