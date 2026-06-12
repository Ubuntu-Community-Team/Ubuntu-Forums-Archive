---
title: "How to install wifi connection without Internet ?"
date: 2007-09-27
forum: Desktop Environments
---

### Post by mhtrinh on 2007-09-27
I have BIG simple problem :
- I can only have internet connection by Wifi with WAP encryption
- My WUSB54GC (wifi card) is not recognized by my Kubuntu 6.06 LTS
- I don't have "make" neither "gcc" 

- I can connect to internet with my Windows partition so i can get packages ...

- How can I get internet working :confused: ?

Thanks a lot for your help !

---

### Post by maybeway36 on 2007-09-27
You probably need to use ndiswrapper. The packages are available by adding the Ubuntu altetrnate CD to your sources.list, but it would probably be easier to hook it up to Ethernet until you get wireless working.

---

### Post by mhtrinh on 2007-09-27
> **maybeway36 said:**
> You probably need to use ndiswrapper. The packages are available by adding the Ubuntu altetrnate CD to your sources.list, but it would probably be easier to hook it up to Ethernet until you get wireless working.

Use Ethernet cable : impossible :(

To install ndiswrapper : what i have to do after burning the Alternate CD ?

Do I have to install some package to use WAP encryption ?

Thanks

---

### Post by pat_can_vault on 2007-11-29
Yes I am having the very same problem... except I don't know much about this! I have a Netgear External USB adapter... help?

---

### Post by mhtrinh on 2007-11-29
I didn't found any solution so I switch to my old distrib : Fedora. With this, I can at least compile drivers ... And that how I made my wifi work finally :popcorn:

Ubuntu without internet = empty shell ... (like other distrib I think ...) 

Some of my friends advise me to install Ubuntu from DVD edition ...

---

### Post by Jouke74 on 2007-11-29
On your (alternate) install CD these packages are available, but they are not installed by default.

These include Build-essential which is required for compiling (meta package for gcc etc.).
Ndiswrapper + common for WIFI.

Just put the CD-rom or DVD you used to install Ubuntu in your CD drive when you start synaptic. Make sure that the CD is available as resource (if you have not unchecked this in the repro list it should be). And install the software. Instead of downloading it will copy the required packages from CD.

No cable required (unless ndiswrapper dislikes your wifi) or steps to other distro's :lolflag:

---

