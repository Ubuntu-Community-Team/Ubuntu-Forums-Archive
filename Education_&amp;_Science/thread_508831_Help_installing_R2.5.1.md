---
title: "Help installing R2.5.1"
date: 2007-07-24
forum: Education &amp; Science
---

### Post by WylieE on 2007-07-24
Hi,
 I have switched to Linux mainly to run R.  I would like to run R 2.5.1, however I am having some difficulties.
I would like to run R2.5.1 in Ubuntu feisty on an AMD64 chip.
I am a total newbie to Linux.
I have successfully compiled 2.5 however, I am not able to figure out how to upgrade the packages.
I am not able to find an R-base-core_2.5.1-1_amd64 or all on the CRAN mirrors.
I can find one on the Ubuntu feisty site, however when I try to install it I get a warning that Dependency is not satisfiable: libc6 
I am pretty convinced I have libc6 installed. 
When I reinstall it with apt-get It says the latest version is currently installed.  
Is this where I should be seeking help for this?   Or are there more appropriate forums?

A second question, until the first gets answered, I would like to run R 2.4.1, which I had no problem getting up and running. 
 However, now that I have tried to install 2.5- whenever I run $sudo R       
I get 2.5.1 if I just run $ R 
 (without sudo) it runs 2.4
I need to run it in sudo so I can install the packages I want to use.  So is there an easy way to uninstall 2.5.
Sorry if these are basic questions, I have had no luck finding the answers on my own.
Thanks in advance for any advice.

---

### Post by Tart on 2007-07-26
I'm also complete noob, but as far as I understand then you do "sudo apt-get" you only get version 2.4.1 and packages for this particular version, unless you add " deb [http://my.favorite.cran.mirror/bin/linux/ubuntu](http://my.favorite.cran.mirror/bin/linux/ubuntu) feisty/" to your /etc/apt/sources.list file. (Or in Add/Remove... -> Third Party software -> Add, , I use "http://lib.stat.cmu.edu/R/CRAN/bin/linux/ubuntu fiesty/" and it works fine for me. Maybe this why you have issues with versions, I know I had with some old packages. 

I hope that this helps

---

### Post by meatpan on 2007-07-26
> **WylieE said:**
> 
I have successfully compiled 2.5 however, I am not able to figure out how to upgrade the packages.


I'm not sure if this is appropriate, but have you tried running 'R CMD INSTALL <package-name>' from the command line, where <package-name> is the .tar.gz file of the desired lib?   It seems like R would understand the build environment enough to compile/install the packages correctly under this scheme.

---

### Post by euler_fan on 2007-07-26
> **meatpan said:**
> I'm not sure if this is appropriate, but have you tried running 'R CMD INSTALL <package-name>' from the command line, where <package-name> is the .tar.gz file of the desired lib?   It seems like R would understand the build environment enough to compile/install the packages correctly under this scheme.

This would be my advice as well . . . while the repos are nice for handling you mainline upgrades, most of R's packages are not available as binaries for Ubuntu.

---

### Post by edoviak on 2007-07-29
You're probably having trouble with the packages because you're running two competing versions of R (2.5.1 and 2.4.1). Might I suggest that you completely uninstall R and start over?

As a side note, I have R 2.5.1 and I don't see any difference between R 2.5.1 and 2.4.1, so you may want to make it easy on yourself stick with what's in the repository. 

While you're at it, don't forget to install the "r-recommended" package! It gives you: KernSmooth, MASS, class, nnet, spatial, boot, cluster, foreign, lattice, mgcv, nlme, rpart and survival.

Also, the best reason to use GNU/Linux is RKWard. Install it and you'll be amazed at how simple and powerful R can be. 

RKWard is a front-end and interactive development environment for R. It provides the console, the script editor, a very clever data editor and a GUI for routine tasks (producing descriptive statistics, correlation matrix, etc.) It also a GUI that will take care of installing and loading packages for you. 

The version in Ubuntu's repository is 0.4.2, but the project really turned a corner recently. You seem adventurous, so install 0.4.6 or 0.4.7a if you can. Here's a thread with my experiences:

[http://ubuntuforums.org/showthread.php?t=483147](http://ubuntuforums.org/showthread.php?t=483147)

Hope this helps,
- Eric

---

