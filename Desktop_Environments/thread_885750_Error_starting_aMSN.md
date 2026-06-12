---
title: "Error starting aMSN"
date: 2008-08-10
forum: Desktop Environments
---

### Post by Nego1987 on 2008-08-10
Hey,

I just installed aMSN but while booting i get the following error:

--------------
Loading TkCxImage failed. This module is needed to run aMSN.
Please compile aMSN first, instructions on how to compile are located in the file INSTALL.
--------------

But the problem is i cant find any INSTALL file and dont know what to do next. Im not a huge Linux expert so hope someone can help me.

greetz

---

### Post by SuperSonic4 on 2008-08-10
have you tried /home/<username>/.amsn and seeing if it's there? Also what version do you have?

The latest version is 0.97.2 and can be found at [http://www.amsn-project.net/linux-downloads.php](http://www.amsn-project.net/linux-downloads.php)

the top one is best for you I imagine, once downloaded right click on it, mark it as executable and double click

*edit*

if you download the new version I'd do ```
sudo apt-get purge amsn
``` which will remove the version you have now

---

### Post by Nego1987 on 2008-08-10
Thought i already done it but i have done it again and with the same result.

```

sudo apt-get install tcl8.5

```

will tell me i have the latest version

---

### Post by fwre01 on 2008-08-10
i would also purge the existing installed version and install the new version. I installed the new version earlier, but had a few problems when trying to compile it. I found this worked...

Install these packages
```
sudo apt-get install g++ tcl8.4 tcl8.4-dev tk8.4 tk8.4-dev tcltls libjpeg62 libjpeg62-dbg libjpeg62-dev libpng12-0 libpng12-dev
```


Then download the new 0.97.2 source code from the aMSN site to /tmp
cd to /tmp and extract the tarball using "tar -xvjf amsn-*.tar.bz2"
cd into the extracted directory and run "./configure"
all being well you should then be able to run "make" then "sudo make install"

---

### Post by Nego1987 on 2008-08-10
Well the installer run correctly? Im not a Linux expert. What do i have to do exactly

---

### Post by fwre01 on 2008-08-10
> **Nego1987 said:**
> Well the installer run correctly? Im not a Linux expert. What do i have to do exactly

What exactly are you trying to do? do you want to remove the existing version and install the new version?

---

### Post by Nego1987 on 2008-08-10
No, i just installed the latest version 0.97

But when starting the program i recieve the error listed above

---

### Post by fwre01 on 2008-08-10
how did u install it? did you install it from the repo's? 0.97 isnt the new version. 0.97.2 is, which i think is only availible as source code

---

### Post by Nego1987 on 2008-08-10
Installed this as executable:
[http://www.amsn-project.net/linux-downloads.php](http://www.amsn-project.net/linux-downloads.php)

---

### Post by fwre01 on 2008-08-10
have u tried running the command i suggested earlier?

```
sudo apt-get install g++ tcl8.4 tcl8.4-dev tk8.4 tk8.4-dev tcltls libjpeg62 libjpeg62-dbg libjpeg62-dev libpng12-0 libpng12-dev
```

---

### Post by Nego1987 on 2008-08-10
Yes, after running the install the error still returns

---

