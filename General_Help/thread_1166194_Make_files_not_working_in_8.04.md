---
title: "Make files not working in 8.04"
date: 2009-05-21
forum: General Help
---

### Post by gymophett on 2009-05-21
When I go to install a package via terminal and need to do a make file, it says it isn't found. I can go in the folder and see the makefile but still can't use it. I'm trying to install a program but can't without make. Do I need to install something in 8.04 to do a make, because I just put 8.04 on this computer yesterday. Thanks for all of your help!

---

### Post by Cheesemill on 2009-05-21
You may need to install the required tools, try the following:
```
sudo apt-get install build-essential linux-headers-`uname -r`
```

Cheesemill

---

### Post by gymophett on 2009-05-21
Cheesemill:
```

bash: uname-r: command not found
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
Package linux-headers is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libemeraldengine0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Hmm. Now what?

---

### Post by baseface on 2009-05-21
are you running ./configure first?

---

### Post by gymophett on 2009-05-21
> **baseface said:**
> are you running ./configure first?

Yes.. I wonder whats wrong.

---

### Post by mcduck on 2009-05-21
> **gymophett said:**
> When I go to install a package via terminal and need to do a make file, it says it isn't found. I can go in the folder and see the makefile but still can't use it. I'm trying to install a program but can't without make. Do I need to install something in 8.04 to do a make, because I just put 8.04 on this computer yesterday. Thanks for all of your help!

Does it say that the file is not found, or that make is not found? Could you post the exact commands you try to run, and resulting errors?

..and make sure you are running the commands in the directory where the makefile is.. ;)

---

### Post by jespdj on 2009-05-21
> **gymophett said:**
> Cheesemill:
...
Hmm. Now what?
There has to be a space between "uname" and "-r":
```
sudo apt-get install build-essential linux-headers-`uname -r`
```

---

### Post by Cheesemill on 2009-05-21
Sorry about the typo, I've edited my first post.

Cheesemill

---

