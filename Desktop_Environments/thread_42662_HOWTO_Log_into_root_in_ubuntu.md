---
title: "HOWTO: Log into root in ubuntu"
date: 2005-06-18
forum: Desktop Environments
---

### Post by mp3guy on 2005-06-18
I was messing around with ubuntu earlier on, and I crashed x, so had to do some repairing. When I was finished i forgot i was in root and just typed startx. To my surprise, ubuntu started up x in the root account, not my own. After that, I just shutdown x, exited root and went back to using ubuntu normally.

---

### Post by Mez on 2005-06-18
**WARNING**: IT IS VERY UNSAFE TO LOGIN TO YOUR SYSTEM AS ROOT: THIS IS WHY UBUNTU COMES WITH SUDO ENABLED AND THE ROOT ACCOUNT DISABLED BY DEFAULT

---

### Post by allforcarrie on 2005-06-19
all the other distros i have used used root so that is how i learned....

---

### Post by TripHammer on 2005-06-19
This will prompt you to set the root password, once set, you can log in as root however as posted earlier, I don't recommend it:


sudo passwd root

---

