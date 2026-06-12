---
title: "VMWare installation issues"
date: 2006-01-17
forum: General Help
---

### Post by conseQuence on 2006-01-17
I'm relatively new to Ubuntu and Linux as a whole so any help is appreciated.

I'm trying to get VMWare player installed on Ubuntu and during the installation process, it cannot find an appropriate vmmon module for my kernel so it asks if i want to try and build one for my system. Now I've made sure that the gcc compiler is installed and the right version and all.

When it goes to compile, it asks for the location of the C header files and defaults to looking in the /usr/src/linux/include directory. When I try to accept it, it says nothing is there. I tried to look for kernel-source packages in synaptic but only found up to kernel version 2.6.11.

I am running kernel version 2.6.12-10-386. Can someone help me find and install these files so I can get VMWare running on my machine?

Thanks,
con.

---

### Post by qferret on 2006-01-17
In synaptic, the new ones are under "linux-source"

Note that VMWare is looking for the headers though....linux-headers

I recently went through it  ;-)

---

### Post by lamego on 2006-01-17
The easy way:

sudo apt-get update
sudo apt-get install build-essential
sudo apt-get install gcc
sudo apt-get install linux-headers-$(uname -r)

---

