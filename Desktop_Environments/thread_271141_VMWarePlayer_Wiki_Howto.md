---
title: "VMWarePlayer Wiki Howto"
date: 2006-10-04
forum: Desktop Environments
---

### Post by dolarsrg on 2006-10-04
Hi everyone!

I've follow this wiki howto to install VMWP:
[https://help.ubuntu.com/community/VMWarePlayerAndWindowsHOWTO](https://help.ubuntu.com/community/VMWarePlayerAndWindowsHOWTO)

At the last step of the sudo apt-get the konsole shows this lines:
```
Starting VMware services:
   Virtual machine monitor                                            failed
   Virtual ethernet                                                   failed
Module vmnet is not loaded.  Please verify that it is loaded before
running this script.

invoke-rc.d: initscript vmware-player, action "start" failed.
```

When I try to run 
# sudo apt-get install vmware-player

A window with this error appear:
Could not open /dev/vmmon: no such file or directory, please make sure...

I've been searching in the forum and I read something about kernel headers, but the wiki doesn't say anything about it and I don't know what to do.

What is the problem? thanks in advance!

---

### Post by dolarsrg on 2006-10-04
I just try to run this command line:
# sudo modprobe vmnet

But the module doesn't exist. So I try:
# sudo apt-get install vmnet

But the package doesn't exist but another package ask for it so it seems it was in some repository. Can it be the problem? :(

---

### Post by anaconda on 2006-10-04
Can't help you with VMWare player, but I installed VMWare server, which is better, because you can also create the virtual machines (and it is also free)

Here is a link to howto:
[http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware+howto](http://www.ubuntuforums.org/showthread.php?t=183209&highlight=vmware+howto)
I followed these instructions and didn't have any problems.

---

### Post by dolarsrg on 2006-10-04
Thanks a lot Anaconda!!!!!!!

I didn't know about another free option of VMWare! I'm gonna install it.

Thanks again!

---

### Post by dolarsrg on 2006-10-04
I've another problem now :( :

When I'm running the installation script it ask me for the linux-headers path to compile the modules. In the repositories we have the linux 2.6.15-23 headers so I gave that path but:

```
The directory of kernel headers (version 2.6.15-23) does not match your running
kernel (version 2.6.15-26-386).  Even if the module were to compile
successfully, it would not load into the running kernel.

```

So, I need the heades and I can't find them in the repositories (I tried debian.com too but I couldn't find them).

What can I do??

---

### Post by anaconda on 2006-10-04
This command installs the kernel headers for your kernel:
```
sudo apt-get install linux-headers-`uname -r`
```
Use copy-paste to get the spelling correctly..

And the kernel headers to your kernel version (or any kernel that is downloaded from the repositories) are in the repositories. I'am running kernel version 2.6.15-27-386, and its headers were also in the repos.

If you cant find them then you have a problem with your sources.list -file.. and you should eneble more repositories.

---

### Post by dolarsrg on 2006-10-04
Thanks indeed anaconda!!!

My sources.list had lines "Comented by the installer because verification faliled" (¿¿¿???) and I didn't realised ](*,) 

Now I've the headers... sorry about the mistake :confused: 

I'm going to continue the install

---

### Post by dolarsrg on 2006-10-04
Great!! It works perfectly!!


Thanks a lot!

---

