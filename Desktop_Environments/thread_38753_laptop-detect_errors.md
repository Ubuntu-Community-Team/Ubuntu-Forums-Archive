---
title: "laptop-detect?? errors"
date: 2005-06-01
forum: Desktop Environments
---

### Post by kittcankitt on 2005-06-01
I am usually able to search these forums (and google, of course) to get any questions I might have answered but this one has me stumped.

Originally I was trying to install vcdimager and kept getting this error..

kck@sdmf:~$ sudo apt-get install vcdimager
Password:
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
libcdio0 libiso9660-0 libvcdinfo0
The following NEW packages will be installed:
libcdio0 libiso9660-0 libvcdinfo0 vcdimager
0 upgraded, 4 newly installed, 0 to remove and 53 not upgraded.
Need to get 0B/724kB of archives.
After unpacking 1524kB of additional disk space will be used.
Do you want to continue [Y/n]? y

Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/libcdio0_0.68-2_i386.deb (--unpack):
unable to open files list file for package `laptop-detect': Input/output error
Errors were encountered while processing:
/var/cache/apt/archives/libcdio0_0.68-2_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

Now, ANYTHING I try to install/upgrade gives me the same error. I am not using a laptop (although from what I've read, laptop-detect does just that...detects whether or not you are) 

I have the latest version of laptop-detect installed and even though I tried re-installing it, I get the same error. (while re-installing..."unable to open files list for laptop-detect...)

If anyone could help me out on this one I'd probably stop  bangin my head against the wall.

Thanks! kck

---

### Post by kittcankitt on 2005-06-02
anyone?  Update:  I tried reinstalling "laptop-detect" but I get the same error.   If I try to remove it, synaptic wants to remove half of the packages installed on my pc? 

Thanks kck

---

### Post by kittcankitt on 2005-06-06
After more searching and reading and trying things, I'm still getting the same error.  No matter what I try in synaptic,aptitude,apt-get, etc, I get nowhere.  

I am really ready to start begging. lol

---

### Post by kittcankitt on 2005-06-07
Ok, now I'm begging for a helping hand.  Anyone?

I also tried installing a package with dpkg and it's the same thing.

---

### Post by mike998 on 2005-06-07
Try doing a dist-upgrade.  By the looks of your code, you have files that aren't upgraded.

---

### Post by kittcankitt on 2005-06-07
Thanks for the suggestion, Mike but it gives me the same error at the first package it tries to install/configure.

unable to open files list file for package `laptop-detect': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/a2ps_1%3a4.13b-4.2ubuntu0.1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)

???

---

### Post by mike998 on 2005-06-07
Okay, after a quick search, I found [this link](http://ubuntuforums.org/archive/index.php/t-12272.html) which may be of some use.

I tried installing the package myself and didn't have any problems.

---

### Post by kittcankitt on 2005-06-07
I had seen the aforementioned link in my search as well but it didn't help.  I have tried cleaning the apt cache, checking my repositories, tried to install something completely non-related, even tried downloading the packages from another source and trying to install, nothing seems to get rid of this "laptop-detect input/output error".  As I mentioned, if I try to uninstall laptop-detect it wants to uninstall three quarters of my system?!

Hopefully this can be resolved without reinstalling because that would be a REAL bitch at this point.  

By the way, my system is for the most part up to date.  With the exceptions of a few programs I added in (ie: abiword, etc) very few components needed updating.

---

### Post by mike998 on 2005-06-07
I was actually referring more to the performing a fsck on your filesystem, just in case there is a problem with that...
Give that a try, and see if it cures the problem.

---

### Post by kittcankitt on 2005-06-08
Sorry about the mix up.  I should have mentioned that I tried that as well.  I appreciate the time and effort you're putting in to my little dilema here Mike.  Hope you have a couple other tricks up your sleeve.


btw, thanks for helping out a fellow Canadian.  Eastern Townships/Quebec

---

### Post by mike998 on 2005-06-08
Unfortunately, I don't really have anything else up my sleeve.  I have googled this myself and it appears that this is usually caused by filesystem problems.

The only other things I might suggest are : if you have multiple kernels installed, removed all but the currently running kernel (*uname -a*  will show the currently running kernel).  Also, you can try *sudo apt-get clean* to see if that helps.

Other than that, I'm at a loss!

---

### Post by kittcankitt on 2005-06-08
Well out of desperation I tried

sudo shutdown -F -r now

again and THIS time it found a slew or errors.  It advised me to run it manually and so I did.  Unfortunately I wasn't prepared for what was to follow.  Alot of errors and a lot of questions (y/n) and to tell you the truth, I didn't know what was what and answered yes to everything.  After a few more reboots and checks I am back onto my desktop.  

Naturally I tried what brought all of this on in the first place (installing vcdimager) and these are the errors I got:

kck@sdmf:~$ sudo apt-get clean
kck@sdmf:~$ sudo apt-get install vcdimager
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  libcdio0 libiso9660-0 libvcdinfo0
The following NEW packages will be installed:
  libcdio0 libiso9660-0 libvcdinfo0 vcdimager
0 upgraded, 4 newly installed, 0 to remove and 73 not upgraded.
Need to get 724kB of archives.
After unpacking 1524kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe libcdio0 0.68-2 [51.6kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe libiso9660-0 0.68-2 [36.6kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe libvcdinfo0 0.7.20-2ubuntu1 [117kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary/universe vcdimager 0.7.20-2ubuntu1 [519kB]
Fetched 724kB in 4s (170kB/s)

Preconfiguring packages ...
(Reading database ...
dpkg: serious warning: files list file for package `laptop-detect' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `eog' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `ed' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `postfix' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `ethtool' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libbz2-1.0' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `openssh-client' missing, assuming package has no files currently installed.
133813 files and directories currently installed.)
Unpacking libcdio0 (from .../libcdio0_0.68-2_i386.deb) ...
Selecting previously deselected package libiso9660-0.
Unpacking libiso9660-0 (from .../libiso9660-0_0.68-2_i386.deb) ...
Unpacking libvcdinfo0 (from .../libvcdinfo0_0.7.20-2ubuntu1_i386.deb) ...
Unpacking vcdimager (from .../vcdimager_0.7.20-2ubuntu1_i386.deb) ...
Setting up libcdio0 (0.68-2) ...

Setting up libiso9660-0 (0.68-2) ...

Setting up libvcdinfo0 (0.7.20-2ubuntu1) ...

Setting up vcdimager (0.7.20-2ubuntu1) ...


All I did afterwards was backtracked in apt-get install --reinstall(ed) all of the above and so far everything seems to be OK.

Thanks again Mike.  The only reason I am posting this is so that maybe someday someone else can learn from it.  **or at least know that it's happened to someone  else**  lol

---

### Post by mike998 on 2005-06-08
Good to see that it solved your problems.

Glad I could help! \\:D/

---

### Post by THEspacemonkey on 2005-07-02
[QUOTE=kittcankitt]Thanks again Mike. The only reason I am posting this is so that maybe someday someone else can learn from it. **or at least know that it's happened to someone else** lol[/QUOTE]
Well, it has happened to someone else. I'm suspecting something in evms that is corrupting the root filesystem at shutdown, as every six or so shutdowns on my laptop evms hangs the console...

The only way to get out of that loop is to force the machine off (holding the power button for what seems like an eternity).

I'm doing everything I can to get evms as disabled as possible on my laptop, and will report back if all my problems suddenly disappear. Gosh I hope this is the problem, as ubuntu is not usable for me when i have to run fsck every six boots (which, for me always seems to happen on a crowded subway with limited battery).

Sure wished evms wasn't a core requirement for ubuntu (hint, hint) :roll:

---

