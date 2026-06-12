---
title: "Terminal - Abort Error"
date: 2006-02-25
forum: Desktop Environments
---

### Post by fidel_26 on 2006-02-25
I'm a newbie.....

I'm trying to add multimedia codecs to my Ubuntu 5.10 installation, and after putting the commands in terminal, I get the following message (after I'm prompted to enter Y/n to continue:

chris@ubuntu:~$ sudo apt-get install gstreamer0.8-lame
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  liblame0
The following NEW packages will be installed:
  gstreamer0.8-lame liblame0
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 187kB of archives.
After unpacking 504kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Abort.

When i type 'Y' and enter, it says abort, and brings me back to my chris@ubuntu: prompt.

I've had this happen on a couple of other install attempts as well....can anyone suggest what I might be doing wrong or a way to fix this?

Thanks,
Chris

---

### Post by taurus on 2006-02-25
See if you can install gstreamer0.8-lame with synaptic!

---

### Post by fidel_26 on 2006-02-25
I guess that will have to be the way around it for any installs where I run into this problem?

---

### Post by greipeip on 2007-02-15
Yes, I am having the same problem when downloading and installing some Deb packages.  I also get the "Want ot continue? [Y/n] and anything I enter just aborts.  But sometimes after a few tries, the installation continues.

---

### Post by greipeip on 2007-02-15
I found the answer to the [Y/n] abort problem that works for me.By typeing man apt-get at the terminal, you can scroll down and find the option -y.  So I used #  sudo apt-get install package_name -y and it skipped through all the [Y/n]. Caution:If you're not sure what you're installing, using -y will not give you any options to abort.

---

