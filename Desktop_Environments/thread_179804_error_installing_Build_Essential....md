---
title: "error installing Build Essential..."
date: 2006-05-20
forum: Desktop Environments
---

### Post by BayGuy27 on 2006-05-20
**When installing build-essential in Synaptic Package Manager, I recieved the following error:**

build-essential:
 Depends: libc6-dev but it is not going to be installed or
	libc-dev

**I then tried to install the libc6-dev package and recieved the following error:**

libc6-dev:
  Depends: libc6 (=2.3.5-1ubuntu12) but 2.3.5-1ubuntu12.5.10.1 is to be installed

Anyone have a way around this or a fix for this? Thanks in advance,

Dave

---

### Post by Sef on 2006-05-20
From the terminal (Applications > Accessories > Terminal)

sudo apt-get update

sudo apt-get upgrade

if that does not help then do this:

sudo apt-get update

sudo apt-get dist-upgrade

That should install it if the first one does not.

---

### Post by aysiu on 2006-05-20
It sounds as if your sources.list is messed up.

Get a fresh list:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

