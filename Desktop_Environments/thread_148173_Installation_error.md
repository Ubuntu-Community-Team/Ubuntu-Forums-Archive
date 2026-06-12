---
title: "Installation error?"
date: 2006-03-21
forum: Desktop Environments
---

### Post by chrisu87 on 2006-03-21
I've tried the Ubuntu Live Cd before and figured it was pretty good, so I decided to install it. However after installed on a partition, all I get is a command line like interface. How do I get to a desktop environment? Thanks for the help!:)

---

### Post by ssalman on 2006-03-21
it looks like you have installed the server version of Ubuntu, if so you need to run the following commands install the graphical interface...

```
sudo apt-get install -f
sudo apt-get update
sudo apt-get install ubuntu-desktop

```

---

