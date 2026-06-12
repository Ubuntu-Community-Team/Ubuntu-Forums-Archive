---
title: "Installing Steam to Play Dota 2 on Ubuntu 14.04 (64bit)"
date: 2015-04-12
forum: Gaming &amp; Leisure
---

### Post by Jouzea on 2015-04-12
Ok first thing, I'm a regular dude who wants to play Dota 2 on ubuntu. I don't understand codes. so please speak to me as if i'm 10. I installed steam on the steam website. but an error occured. So i tried fixing it and now this is wat happens when i ran it, terminal popped with these text:
Steam needs to install these additional packages:
libgl1-mesa-dri:i386, libgl1-mesa-glx:i386, libc6:i386
[sudo] password for jouzea:

[FONT=arial]So when i enter my password these are the text:[/FONT]

W: GPG error: [http://bn.archive.ubuntu.com](http://bn.archive.ubuntu.com) trusty Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libgl1-mesa-dri:i386 : Depends: libdrm-intel1:i386 (>= 2.4.48) but it is not going to be installed
                        Depends: libexpat1:i386 (>= 2.0.1) but it is not installable
                        Depends: libllvm3.4:i386 but it is not installable
                        Depends: libstdc++6:i386 (>= 4.6) but it is not installable
                        Recommends: libtxc-dxtn-s2tc0:i386 but it is not installable or
                                    libtxc-dxtn0:i386 but it is not installable
 libgl1-mesa-glx:i386 : Depends: libglapi-mesa:i386 (= 10.1.3-0ubuntu0.4)
                        Depends: libx11-6:i386 (>= 2:1.4.99.1) but it is not installable
                        Depends: libx11-xcb1:i386 but it is not installable
                        Depends: libxcb-dri2-0:i386 (>= 1.8) but it is not installable
                        Depends: libxcb-dri3-0:i386 but it is not installable
                        Depends: libxcb-glx0:i386 (>= 1.8) but it is not installable
                        Depends: libxcb-present0:i386 but it is not installable
                        Depends: libxcb-sync1:i386 but it is not installable
                        Depends: libxcb1:i386 (>= 1.9.2) but it is not installable
                        Depends: libxdamage1:i386 (>= 1:1.1) but it is not installable
                        Depends: libxext6:i386 but it is not installable
                        Depends: libxfixes3:i386 but it is not installable
                        Depends: libxshmfence1:i386 but it is not installable
                        Depends: libxxf86vm1:i386 but it is not installable
                        Depends: libudev1:i386 but it is not going to be installed or
                                 libudev0:i386 but it is not installable
 qtdeclarative5-qtfeedback-plugin : Depends: libqt5feedback5 but it is not going to be installed
 unity-control-center : Depends: libcheese-gtk23 (>= 3.4.0) but it is not going to be installed
                        Depends: libcheese7 (>= 3.0.1) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
Press return to continue: 

Can anyone help me please. T.T

---

### Post by Jouzea on 2015-04-12
Update:

I followed the instructions here: [http://ubuntuforums.org/showthread.php?t=2233005](http://ubuntuforums.org/showthread.php?t=2233005)

---

### Post by ajgreeny on 2015-04-12
So, please, if this is now solved, and it is not clear if that is so, can you use the **Thread Tools** menu at the top and mark it as such.

---

### Post by Jouzea on 2015-04-12
Aaand Nope it doesn't work.

---

### Post by Jouzea on 2015-04-13
Thought people will be helpful here. :(
Additional info, i installed ubuntu in my External Hard Drive

---

### Post by QIII on 2015-04-13
Hello!

We are neither conjurers of magical spells nor readers of crystal balls.   Like you, we are "regular dudes" and "dudettes".

Your initial post says:

> I installed steam on the steam website. but an error occured. So i tried  fixing it and now this is wat happens when i ran it, terminal popped  with these text:

If you could tell us

1.  The initial error that occurred.

2.  What you did to try to "fix it".

we might be able to start with some diagnosis rather than stabs in the dark.

We would certainly like to help, but we can only work with the information given.  If it is incomplete, we cannot even begin.  There are a couple of fairly obvious things to try, but it would be nice to know what has gone on before.

---

### Post by wally8 on 2015-04-16
i have the same problem ... same errors .. so far nothing worked . Any luck on your side ?

---

### Post by sffvba[e0rt on 2015-04-19
There is a bug report about this - [https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/1424263](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/1424263)

Work around in comment 6 - [https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/1424263/comments/6](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/1424263/comments/6)

---

### Post by priyesh nambiar on 2015-09-17
Same problem I ran thru and am also a newbie to Ubuntu and hardcore fan of Dota too... I fixed my issue with,

"sudo apt-get install libgl1-mesa-glx-lts-utopic:i386"

---

### Post by charleswmanuel on 2016-05-23
I'm having a similar issue, however I just can't get Dota 2 to open...all other games are fine. what code do you all need to see to help me? I'm getting the Missing executable glitch...

---

