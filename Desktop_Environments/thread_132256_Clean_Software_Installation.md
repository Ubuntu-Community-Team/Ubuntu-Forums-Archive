---
title: "Clean Software Installation"
date: 2006-02-17
forum: Desktop Environments
---

### Post by mogliii on 2006-02-17
Hi,

I am trying hard to get rid of windows and get used to Linux. I already had Kubuntu 5.04 installed, but I kinda messed it up. So I erased everything (secured home folder), and installed a fresh Breezy (Kubuntu 5.10).

But what anoyed me with my last installation:
It seemed I didnt have any control when installing software.

I mean not the packages you can install by apt (works fine and I love it) but when you download an archive, and then you make the procedure of "make install" and  "./install" and everything. Hope you know what I mean.

So my problem was: I wanted to install freeciv for example. Downloaded it to an directory, for example /home/Download/freeciv and unpacked it. Then I had in that directory the archive, and an directory with the unpacked data.

Then I entered the directory and executed the commands like "make install" and so on. I just followed the insturctions on their homepage. But after all it turned out, that everything was still in that directory after installation. This means, that freeciv is installed in /home/Downloads/freeciv/... 

That not perfect, I want it to be installed on my root partition.

So my questions:
1) In which step can I determin, where the final install folder will be

2) How can I remove the unpacked, installation files

Its just my understanding of a clean system, that I should be able to control this.

---

### Post by Jucato on 2006-02-18
by default, configure && make && make install process installs files in the different directories (like /usr/bin or /usr/local, etc.) Unless you tell it otherwise, it won't install anything in your home directory. 

The things that are in your unpacked directory are the files that were created/needed to compile and install the program. It MIGHT be safe to delete them. The reason I said might was that I've read somewhere that keeping those unpacked directory might be good if you want to run "make uninstall" someday, as this is the only way to uninstall them properly (unlike .deb files which can be uninstalled through dpkg or apt-get).

---

### Post by sargo on 2006-02-18
You can use CheckInstall. The normal sequence is ./configure && make && make install, with this application the sequence is:

./configure
make
[sudo] checkinstall

This action makes a .deb package and install it. After that you can uninstall the .deb with apt, dpkg, ...

Sorry for my English

---

### Post by Jucato on 2006-02-18
ey thanks for the tip sargo! I learned something today! :D

---

