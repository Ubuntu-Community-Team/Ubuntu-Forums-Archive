---
title: "Serious problem with compiling kernel"
date: 2006-06-26
forum: Desktop Environments
---

### Post by Dark Shikari on 2006-06-26
I followed the instructions in [this thread]("http://www.ubuntuforums.org/showthread.php?t=157560") to the letter to compile and install the 2.6.16 kernel for my Dapper installation.

First, I went with a totally stripped down kernel config.  It booted up with the new kernel and said that it can't find the nVidia kernel module.  So I go back and turn on some things I disabled, thinking they broke the nVidia kernel module.

I try again, less stripped down.  Same problem.

Then I try again... *with no settings changed from my original kernel config!*

And I *get the same goddamned error*.

What in the heck is going on?  How can a kernel compiled with the exact same settings as a working one have this weird problem?

(If you're wondering, I installed the nVidia driver manually with apt-get previously, and it worked just fine)

---

### Post by w1z4rd on 2006-06-26
Im having similar problems with three of my nvida boxes, they were working, and now i issues every time i boot up now, cause all of a sudden they "dont work"

whats goin on with that? a friend mentioned something about the new driver not in the restricted zone or something like that...

---

### Post by Dark Shikari on 2006-06-26
A friend just answered this for me.  For w1z4rd and the like, here's the answer:

[17:45] sg1bc: apt-get install module-assistant
[17:46] sg1bc: m-a prepare
[17:46] sg1bc: then m-a a-i nvidia
[17:47] sg1bc: the m-a a-i nvidia should be ran in the new kernel
[17:47] sg1bc: (booted to it)
[17:48] sg1bc: that will make a .deb and put it in /usr/src
[17:48] sg1bc: then install that
[17:48] sg1bc: dpkg -i /blahpath
[17:48] sg1bc: then depmod -a
[17:48] sg1bc: the modprobe nvidia
[17:48] sg1bc: then /etc/init.d/gdm start
[17:48] sg1bc: and X will magic work

---

### Post by w1z4rd on 2006-06-26
thank you!

---

