---
title: "su  mode"
date: 2006-06-20
forum: Desktop Environments
---

### Post by metalsam on 2006-06-20
How do i enable su ?

I typed su like i would in FC4, put in my password, and it rejected me!

Ubuntu only asks for one password at setup and thats the one  i entered. 

Is there a default password or something i need to enable?

---

### Post by Gustav on 2006-06-20
Use sudo instead, [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by metalsam on 2006-06-20
so its impossible to become root in terminal ?

---

### Post by Gustav on 2006-06-20
Use 'sudo -s' (or 'sudo -i' or 'sudo bash' or 'sudo su') to get permanent root rights.

---

### Post by metalsam on 2006-06-20
thanks :)

I was thinking i was going to have to change distro for a minute there :P

---

### Post by jgcamp99 on 2006-06-20
Sudo is a feature for doing it one way. You can always reenable the root to login if you so desire. Having both methods at your choice isn't a bad thing. The link above is easy, maybe takes a couple of minutes if that ?

---

### Post by Gustav on 2006-06-21
Securitywise it is not that good to have both sudo and su enabled since that gives evil people two ways of doing evil things to your computer. 

Especially if you enable login as root since then the evil people don't have to guess your username, just your root password.

(Although I'm no security expert so I might be wrong :))

---

### Post by metalsam on 2006-06-21
sudo - s is almost instant :)

theres another one you can sudo -i i think. Opens a fresh terminal session outside of your filesystem - all your files disapear when you start it. Seems a but pointless

---

