---
title: "Streamtuner for Kubuntu?"
date: 2005-04-30
forum: Desktop Environments
---

### Post by drum on 2005-04-30
Please, what's the best way to get my favourite program--Streamtuner.
I can't "apt" it and it's not in Kynaptic. Maybe put another mirror in "sources" file?
Thanks

---

### Post by SGC on 2005-04-30
**Uncomment the following in your sources file (/etc/apt/sources.list):**

[http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

**then:**

sudo apt-get update


**then:**

sudo apt-get install streamtuner

---

### Post by drum on 2005-04-30
Thanks SGC,
Streamtuner works fine. Now I've got The Goon Show and all my jazz stations online  :) 

I edited the /etc/apt/sources.list with nano (nano -w) which I learned from installing Gentoo.

Regards

---

