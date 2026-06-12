---
title: "How to remove unwanted programs"
date: 2006-01-29
forum: Desktop Environments
---

### Post by jimw on 2006-01-29
I had to reinstall Ubuntu the other night, and it has come back without Synaptec.

I also now have two versions of OpenOffice on my computer, one being the ancient 1.1.5.

Trying to uninstall it through apt-get gives me the following:

$ sudo apt-get remove OpenOffice.org1.1.5
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package OpenOffice.org1.1.5

I am several long steps short of computer literate, so I'm willing to bet that I've missed out on something.  Can anyone tell me what it is?

JimW

---

### Post by xristos on 2006-01-29
you can install synaptic with
```
sudo apt-get install synaptic
```
or
you can search for the correct name of any packet you want with
```
sudo apt-cache search search_string
```

---

### Post by jimw on 2006-01-29
you can install synaptic with
Code:

sudo apt-get install synaptic

or
you can search for the correct name of any packet you want with
Code:

sudo apt-cache search search_string

Thaks.  That's helped me a lot!

JimW

---

