---
title: "How to make the development enviroment for Xubuntu"
date: 2007-05-07
forum: Desktop Environments
---

### Post by zeusstar on 2007-05-07
I have installed a new Xubuntu using live CD.  I find it have no gcc and make execute file. So I start the Synaptic, and find gcc-3.3-base and gcc-4.0-base have installed.

I have run the command "sudo apt-get -f -install" also , and find there is no installitaion again.

How can I configure it to make gcc and "make " work?:)

---

### Post by mythik on 2007-05-07
if you install build-essential, since gcc is a dependancy, it'll get installed.  I'm not exactly 100% what build-essential does, I believe I had to get it when manually installing a .deb of pidgin.  HTH.

---

### Post by trippyd on 2007-05-07
Just do:

sudo aptitude install build-essential

it is a virtual package containing the dev tools, including gcc

---

### Post by zeusstar on 2007-05-08
> **mythik said:**
> if you install build-essential, since gcc is a dependancy, it'll get installed.  I'm not exactly 100% what build-essential does, I believe I had to get it when manually installing a .deb of pidgin.  HTH.

Hi, mythik,
     I do not understand your mean. Is your mean that I should install a .deb package? What 's .deb and .HTH?

---

### Post by zeusstar on 2007-05-08
> **trippyd said:**
> Just do:

sudo aptitude install build-essential

it is a virtual package containing the dev tools, including gcc

Hi, I have done that, but it prompt that it can not find the available build-essentail version, so that there is 0 package was installed.

Do you know how to resolve the issue?

---

