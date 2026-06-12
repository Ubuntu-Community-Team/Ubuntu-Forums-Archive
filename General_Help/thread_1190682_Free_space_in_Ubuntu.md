---
title: "Free space in Ubuntu"
date: 2009-06-18
forum: General Help
---

### Post by vishalag on 2009-06-18
Hi All,

I have installed ubuntu on a really small HD space.(5 GB). Now I am in a problem that I dont have any space left on device so nothing works.

Can anyone tell me if I can delete some things from file systems which will not affect my performance.

I need these things working in my ubuntu:

1. Internet
2. Eclipse 
3. Text Editor

---

### Post by asdfhjkla on 2009-06-18
Hi,

Read [this]("http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html") for some advice on removing unnecessary files. This *might* free up some space.

---

### Post by coffeecat on 2009-06-18
If you only need...

> **vishalag said:**
> 1. Internet
2. Eclipse 
3. Text Editor

... then 5GB is more than enough. I've got Jaunty NBR running on my Asus EeePC with a 4GB flash hard drive. I've uninstalled nothing, installed a couple of apps and still have over 1GB free. So...

Have you emptied the trash?
Have you backed up and removed any personal files you don't need day-to-day?
If you only need a text editor, do you need Open Office? If you don't, uninstall all Open Office components. This will free at least a couple of hundred MB, if not more.

And lastly. This wasn't in the main part of asdfhjkla's link, but one of the commenters mentions this. You can free up space by emtying the apt package cache with

```
sudo apt-get clean
```

---

### Post by tomd123 on 2009-06-18
> **vishalag said:**
> Hi All,

I have installed ubuntu on a really small HD space.(5 GB). Now I am in a problem that I dont have any space left on device so nothing works.

Can anyone tell me if I can delete some things from file systems which will not affect my performance.

I need these things working in my ubuntu:

1. Internet
2. Eclipse 
3. Text Editor

I think your home folder is killing your space. I have a TON of stuff installed including dev-packages, graphics programs, games, big text editors, windows restricted package, audio packages, and etc... and I'm using just under 4GiB on / but my /home contains about 40GiB of files :P

---

### Post by rushikesh988 on 2009-06-18
> **vishalag said:**
> Hi All,

I have installed ubuntu on a really small HD space.(5 GB). Now I am in a problem that I dont have any space left on device so nothing works.

Can anyone tell me if I can delete some things from file systems which will not affect my performance.

I need these things working in my ubuntu:

1. Internet
2. Eclipse 
3. Text Editor
bro you should boot your PC in recovery mode of ubuntu .. and cleat that all garbage from your PC

---

