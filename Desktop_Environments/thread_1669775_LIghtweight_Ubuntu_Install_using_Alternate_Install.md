---
title: "LIghtweight Ubuntu Install using Alternate Install CD"
date: 2011-01-18
forum: Desktop Environments
---

### Post by austinium on 2011-01-18
Hi,

I am trying to do a 'light' install of Ubuntu 10.04 using the alternate install CD. Here is how i am planning to do it:

1. Perform a console only installation(Standard system only on d-i tasksel)
2. Install gnome-core
3. Then install the packages i need using apt. 

Now, here are the questions:
1. Would such an installation lead have any significant performance(RAM usage) advantage over a full fledged installation? 

2. Is there a way i could install gnome-core from the installation CD instead of downloading them from the repository? 

3. Would installing just gnome-core mean that synaptic & update-manager wouldn't be available? i am hoping that it wouldn't be the case :| I checked their dependencies from packages.ubuntu.com, it doesn't look like they need gnome-desktop-environment to be installed first.

4. Would such an install have any more device driver related issues (eg.display drivers) than a regular install?

I got the idea after reading the following blog posts
[http://kmandla.wordpress.com/2010/03/22/build-a-lighter-gnome-in-ubuntu/](http://kmandla.wordpress.com/2010/03/22/build-a-lighter-gnome-in-ubuntu/)
[http://kmandla.wordpress.com/2010/03/21/build-a-lightweight-graphical-system-in-ubuntu/](http://kmandla.wordpress.com/2010/03/21/build-a-lightweight-graphical-system-in-ubuntu/)


thanks in advance :)

---

### Post by austinium on 2011-01-19
^bump~

---

### Post by Cheesehead on 2011-01-19
Depending on your hardware, your optimized solution might have a small performance improvement...or not. It will be an interesting test.

Instead of gnome-core, you may do better simply adding the packages your *really* want as a user (like firefox or VLC), and letting the package manager figure out what to get. Gnome-core, for example, will pull in eog and gedit.

If you really want to build a light system, you need to be familiar with apt-get or aptitude and other command-line tools for package management. Else you will be working much too hard if you make a mistake.

The easy way around display driver issues and many other headaches is to test your environment in a Virtual Machine. The hour or so to install a VM system and learn to use it will save you *days* of frustration!

For example, you can do a baseline standard install in the VM environment, and run a set of baseline tests. Then you can do your light install and compare to see if there is a significant performance improvement. All without mucking with your real partitions or display drivers or system. When you make a mistake, simply roll back and try again. You can see if all your changes are worthwhile before actually carrying them out on your real system.

---

### Post by Cheesehead on 2011-01-19
Just tested it - building a lightweight machine inside a VM takes less than an hour.

1) sudo apt-get install virtualbox-ose
2) download the 10.10 minimal install image (12MB) from [http://archive.ubuntu.com/ubuntu/dists/maverick/main/installer-i386/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/maverick/main/installer-i386/current/images/netboot/mini.iso)
3) Open VirtualBox, create a new Ubuntu machine, add the mini.iso to the virtual CD Drive, and boot it from the mini.iso
4) Install. Don't walk away - it asks questions during the install.  Requires network access. Takes about 25 minutes, depending on network speed.
5) Remove the mini.iso from the virtual CD Drive, and boot the virtual machine live - it will take you to a command prompt - no GUI is installed yet.
6) Take a snapshot of your fresh Ubuntu-Standard virtual install.
7) sudo-apt-get install mypackage1 mypackage2 mypackage3 etc. Now that you have a first snapshot to roll back to, you can muck up your new virtual system all you like.

---

### Post by austinium on 2011-01-20
the trouble with using a mini iso image to start off with is that i am beind a network proxy, i use cntlm/ntlmaps on my other machines for package installation but in this case that is not an option. Thats the reason i thought i will start off from a shell(no gui) installation and build it up from there.

[http://username: password@ip: port/](http://username: password@ip: port/) gives me a "bad mirror" error. (space is intentional, to avoid :P)

update: they've taken tasksel off in the alternate installer, so anyone who is looking for a d-i like tasksel to do a command line system installation will have press F4 at boot and then select the option provided. The default is to do a GUI installation.

---

