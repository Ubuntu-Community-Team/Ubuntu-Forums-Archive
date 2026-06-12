---
title: "Can't find kernel update  2.6.28-11-generic"
date: 2009-05-08
forum: General Help
---

### Post by MrPolite on 2009-05-08
Hi
I need to install version 2.6.28-11-generic.
I've tried doing
[B]sudo apt-get install linux-image-2.6.28-12
[/B]
but it can't find the package. The reason i'm looking for this particular message is because I need linux-image-debug package to be able to run SystemTap.

any help is much appreciated!

---

### Post by Kevbert on 2009-05-08
Welcome to Ubuntu.
What version of Ubuntu are you currently using ?
Please post the terminal output of 
```
lsb_release -a
uname -a
```
Also what software sources have you enabled ?

---

### Post by MrPolite on 2009-05-08
Hi, thanks for your response

```
Distributor ID:    Ubuntu
Description:    Ubuntu 9.04
Release:    9.04
Codename:    jaunty
```
```
Linux kourosh-ubunto9 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux
```> **Kevbert said:**
> Also what software sources have you enabled ?
I'm not sure what you mean by that.


EDIT: I'm not a linux person... Just to clarify why i want this: I'm trying to get SystemTap working, and it's missing kernel debug information. The only debug info that i can find ([http://ddebs.ubuntu.com/pool/main/l/linux/](http://ddebs.ubuntu.com/pool/main/l/linux/)) is for version **2.6.28-12.** That's why i think i need to upgrade the kernel first then use the available debug info.

---

### Post by dcstar on 2009-05-08
> **MrPolite said:**
> 
.........
EDIT: I'm not a linux person... Just to clarify why i want this: I'm trying to get SystemTap working, and it's missing kernel debug information. The only debug info that i can find ([http://ddebs.ubuntu.com/pool/main/l/linux/](http://ddebs.ubuntu.com/pool/main/l/linux/)) is for version **2.6.28-12.** That's why i think i need to upgrade the kernel first then use the available debug info.

There is no point whatsoever using a debug version of a kernel that is not the kernel you are running.

If you want a debug kernel, compile your own with that compile option enabled - there are many detailed FAQs that can tell you how to compile kernels.

---

### Post by Kevbert on 2009-05-08
Software Sources are the repositories (where the packages are stored) which allow you to download software to your PC. These can be selected either by going to System-Administration-Software Sources, or by editing your /etc/apt/sources.list file.
If you really want kernel 2.6.28.12 you can get it as follows:
1) Go into Software Sources (see above).
2) Select Settings, Repositories.
3) A new window will open. Select the Updates tab.
4) Make sure Proposed updates is ticked (**software may not be stable though!**)
5) Click on Close.
6) Click on the top left Reload button (to update the list of available packages).
7) Now go to Applications-Accessories-Terminal
8) Enter ```
sudo apt-get install linux-image-generic
```
This will install the latest kernel (which may be unstable!!!).

---

### Post by MrPolite on 2009-05-08
> **Kevbert said:**
> Software Sources are the repositories (where the packages are stored) which allow you to download software to your PC. These can be selected either by going to System-Administration-Software Sources, or by editing your /etc/apt/sources.list file.
If you really want kernel 2.6.28.12 you can get it as follows:
1) Go into Software Sources (see above).
2) Select Settings, Repositories.
3) A new window will open. Select the Updates tab.
4) Make sure Proposed updates is ticked (**software may not be stable though!**)
5) Click on Close.
6) Click on the top left Reload button (to update the list of available packages).
7) Now go to Applications-Accessories-Terminal
8) Enter ```
sudo apt-get install linux-image-generic
```This will install the latest kernel (which may be unstable!!!).

Thanks a lot! that solved it, and system tap is working fine now :) :)

---

