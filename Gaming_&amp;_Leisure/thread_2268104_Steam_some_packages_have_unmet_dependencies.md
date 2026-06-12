---
title: "Steam some packages have unmet dependencies"
date: 2015-03-06
forum: Gaming &amp; Leisure
---

### Post by polochamps on 2015-03-06
Hi,

I just recently installed Steam on a freshly installed Ubuntu 14.04.2. This prompted on the terminal and went through the installation.
Would it cause any conflicts? And why it happened?
Thank you

```
Steam needs to install these additional packages: 
    libgl1-mesa-dri:i386, libgl1-mesa-glx:i386, libc6:i386
[sudo] password for polochamps: 
....................................................................................................................
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libgl1-mesa-glx:i386 : Depends: libglapi-mesa:i386 (= 10.1.3-0ubuntu0.3)
 unity-control-center : Depends: libcheese-gtk23 (>= 3.4.0) but it is not going to be installed
                        Depends: libcheese7 (>= 3.0.1) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
Press return to continue: 

```

---

### Post by Bucky Ball on 2015-03-06
Did you:

```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

... first? Please do so and try again. Report any and all errors.

---

### Post by polochamps on 2015-03-06
> **Bucky Ball said:**
> Did you:

```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

... first? Please do so and try again. Report any and all errors.

Just this one "sudo apt-get update". The sudo apt-get upgrade was already done via gui "software updater".
Please correct me if I understand it correctly that you want me to run those commands? Or just asking?
I'm just being cautious because the last time I run "sudo apt-get autoremove" it screwed me up.

Thank you

---

### Post by mc4man on 2015-03-06
run this & compare installed version of first vs candidate of the i386, they must match exactly
```

apt-cache policy libgl1-mesa-glx libgl1-mesa-glx:i386
```

---

### Post by polochamps on 2015-03-06
> **mc4man said:**
> run this & compare installed version of first vs candidate of the i386, they must match exactly
```

apt-cache policy libgl1-mesa-glx libgl1-mesa-glx:i386
```

None installed?

```
polochamps@POLOCHAMPS-DESK:~$ apt-cache policy libgl1-mesa-glx libgl1-mesa-glx:i386
libgl1-mesa-glx:
  Installed: (none)
  Candidate: 10.1.3-0ubuntu0.3
  Version table:
     10.1.3-0ubuntu0.3 0
        500 http://ph.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
     10.1.0-4ubuntu5 0
        500 http://ph.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
libgl1-mesa-glx:i386:
  Installed: (none)
  Candidate: 10.1.3-0ubuntu0.3
  Version table:
     10.1.3-0ubuntu0.3 0
        500 http://ph.archive.ubuntu.com/ubuntu/ trusty-updates/main i386 Packages
     10.1.0-4ubuntu5 0
        500 http://ph.archive.ubuntu.com/ubuntu/ trusty/main i386 Package
```

---

### Post by mc4man on 2015-03-06
Then you're likely on the mesa-lts-utopic version of 14.04.2
To d. check on Installed for first & avail. candidate  on i386
```
apt-cache policy libgl1-mesa-glx-lts-utopic libgl1-mesa-glx-lts-utopic:i386
```

---

### Post by polochamps on 2015-03-06
> **mc4man said:**
> Then you're likely on the mesa-lts-utopic version of 14.04.2
To d. check on Installed for first & avail. candidate  on i386
```
apt-cache policy libgl1-mesa-glx-lts-utopic libgl1-mesa-glx-lts-utopic:i386
```

```
polochamps@POLOCHAMPS-DESK:~$ apt-cache policy libgl1-mesa-glx-lts-utopic libgl1-mesa-glx-lts-utopic:i386
libgl1-mesa-glx-lts-utopic:
  Installed: 10.3.2-0ubuntu1~trusty2
  Candidate: 10.3.2-0ubuntu1~trusty2
  Version table:
 *** 10.3.2-0ubuntu1~trusty2 0
        500 http://ph.archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
        100 /var/lib/dpkg/status
libgl1-mesa-glx-lts-utopic:i386:
  Installed: (none)
  Candidate: 10.3.2-0ubuntu1~trusty2
  Version table:
     10.3.2-0ubuntu1~trusty2 0
        500 http://ph.archive.ubuntu.com/ubuntu/ trusty-updates/main i386 Packages
        500 http://security.ubuntu.com/ubuntu/ trusty-security/main i386 Packages
```

---

### Post by mc4man on 2015-03-06
Well try - 
```
sudo apt-get install libgl1-mesa-glx-lts-utopic:i386
```

---

### Post by polochamps on 2015-03-06
> **mc4man said:**
> Well try - 
```
sudo apt-get install libgl1-mesa-glx-lts-utopic:i386
```

Just a clarification. Do I still need this even if I'm running the Nvidia proprietary driver?

Thank you

---

### Post by mc4man on 2015-03-06
> **polochamps said:**
> Just a clarification. Do I still need this even if I'm running the Nvidia proprietary driver?

Thank you

I don't use steam so can't say other than it seems to be requiring the 32 bit version so I'd say yes

---

### Post by Bucky Ball on 2015-03-06
> **polochamps said:**
> 
I'm just being cautious because the last time I run "sudo apt-get autoremove" it screwed me up.

Thank you

Run these three then:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

... without autoremove command, then, if you get no errors, to install 32bit libraries (as it appears not to drag them in):

```
sudo apt-get install lib32z1 lib32ncurses5 lib32bz2-1.0 lib32stdc++6
```

... then:

```
sudo apt-get install steam -y
```

---

### Post by polochamps on 2015-03-06
> **mc4man said:**
> I don't use steam so can't say other than it seems to be requiring the 32 bit version so I'd say yes

Hmmm. There is an option on Steam in which it will verify your games for data consistency and found out that it wasn't working until I installed the libraries you pointed out.
Voila. Problem solved!

Thank you very much man!

---

### Post by Bucky Ball on 2015-03-06
You're fixed? If so, good news and please mark the thread as solved (see the second link in my signature). ;)

---

### Post by polochamps on 2015-03-06
> **Bucky Ball said:**
> You're fixed? If so, good news and please mark the thread as solved (see the second link in my signature). ;)

Oh I almost forgot to mark it.

Thank you good sir!

---

### Post by underskyzx on 2015-04-07
> **Bucky Ball said:**
> Run these three then:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

... without autoremove command, then, if you get no errors, to install 32bit libraries (as it appears not to drag them in):

```
sudo apt-get install lib32z1 lib32ncurses5 lib32bz2-1.0 lib32stdc++6
```

... then:

```
sudo apt-get install steam -y
```

It worked!

Tyvm!

---

### Post by chronictron on 2015-06-23
> **Bucky Ball said:**
> Run these three then:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

... without autoremove command, then, if you get no errors, to install 32bit libraries (as it appears not to drag them in):

```
sudo apt-get install lib32z1 lib32ncurses5 lib32bz2-1.0 lib32stdc++6
```

... then:

```
sudo apt-get install steam -y
```

Many thanks, this was a perfect solution that worked for me in Lubuntu 14.04.2

---

### Post by Kereltis on 2015-06-25
> **polochamps said:**
> Just a clarification. Do I still need this even if I'm running the Nvidia proprietary driver?

Thank you

Yes, Steam needs certain 32Bit Libs to run on a 64Bit system.

This seems to be the same issue as this post: [http://ubuntuforums.org/showthread.php?t=2233005](http://ubuntuforums.org/showthread.php?t=2233005)

Another solution can be found on Ask Ubuntu here: [http://askubuntu.com/questions/257084/how-do-i-install-steam-on-a-64bit-system](http://askubuntu.com/questions/257084/how-do-i-install-steam-on-a-64bit-system)

---

### Post by djtxyz on 2015-12-01
_**Many Thanks! **_ :D Worked for my "spare parts" machine - AMD Opteron 180, AMD R9-270 vid card w/ AMD Radeon Proprietary drivers installed, Ubuntu 14.04 LTS. 

Followed the "Bucky Ball" hack, but did manually first *autoremove* files when suggested by the Ubuntu dialog box, without any problems.  I did reboot (as suggested by Ubuntu) after each command.

btw - can save some funky typing by highlighting suggested commands, right-click to copy, then in the terminal right-click to paste.

---

### Post by keithwwalker on 2016-01-02
Worked perfectly on my new Asus GR8 (64 bit) with 14.04 installed.
Thank you very much!!!

> **Bucky Ball said:**
> Run these three then:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

... without autoremove command, then, if you get no errors, to install 32bit libraries (as it appears not to drag them in):

```
sudo apt-get install lib32z1 lib32ncurses5 lib32bz2-1.0 lib32stdc++6
```

... then:

```
sudo apt-get install steam -y
```

---

### Post by e1ektrob0y on 2016-01-03
This doesn't work for me. When I run 

```
sudo apt-get install steam -y
```

I get the following

```
The following packages have unmet dependencies:
 steam:i386 : Depends: libgl1-mesa-dri:i386
              Depends: libgl1-mesa-glx:i386
E: Unable to correct problems, you have held broken packages.

```

---

### Post by tatsujb on 2016-04-17
> **e1ektrob0y said:**
> This doesn't work for me. When I run 

```
sudo apt-get install steam -y
```

I get the following

```
The following packages have unmet dependencies:
 steam:i386 : Depends: libgl1-mesa-dri:i386
              Depends: libgl1-mesa-glx:i386
E: Unable to correct problems, you have held broken packages.

```
same.

I have ubuntu 14.04 64bit on laptop nvidia driver "Legacy binary driver - version 304.131 from nvidia-304-updates (proprietary)" this along with the one without updates and Xorg are the only ones that works. anything higher will give a black screen.


libGL.so.1 and a superior version is installed but steam keeps complaining (when I install it via the software centre) that it isn't.

I get all the errors : steam opening a terminal window to install two 32 libraries that it fails to (TWICE)

and then both the installer and steam itself tell me about the missing about the missing libGL.so

but when i try to install steam via the terminal :
```
sudo apt-get install steam -y
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:


The following packages have unmet dependencies:
 steam:i386 : Depends: libgl1-mesa-dri:i386
              Depends: libgl1-mesa-glx:i386
E: Unable to correct problems, you have held broken packages.

```

I've tried eight different methods and all the different threads about this all over the web.

---

### Post by Boris786 on 2016-05-19
I have had this as well on Ubuntu 14.04LTS - 64 bit. It did not affect the running of steam but was a nuisance. Seems to be a very well known problem and have seen thread on these forums were it is closed as solved. I read that thread and could not see solution, at least for originator. I resolved with: 

sudo apt-get install libgl1-mesa-dri-lts-trusty:i386 libgl1-mesa-glx-lts-trusty:i386 libc6:i386
Which I found on ask Ubuntu I think. I think it goes under bug: [https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/1424263](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/1424263)

As far I can tell this is not resolved - very off putting for newbie who installs Ubuntu and then wants to play a steam game. Might they give up and install windows?

---

### Post by QDR06VV9 on 2016-05-19
Thread Moved to Gaming & Leisure

---

