---
title: "Help with Apps"
date: 2005-11-24
forum: Desktop Environments
---

### Post by windowsXuser on 2005-11-24
Hello Everyone,

I am another new noobie to the forum and to the Linux community.
I have recently installed Kubuntu 5.10 breezy badger and think its great so far.  I have taken a few linux courses, but were on based on rpm and not debian. Something to get used to.

I have a question about installing new software.  I have tried installing some software sucessfully, but how do you run the program after its been downloaded in your home directory.  Does it need to be compiled?

Thanks,
blair..

---

### Post by windowsXuser on 2005-11-24
I am trying to install KDevelop and am having some problems.

I extracted the file kdevelop-3.2.1.tar.gz2 to the desktop then
blair@kubuntu:~/kdevelop-3.2.1$ ./configure

it runs great til it hits this error message..

configure: WARNING: libjpeg not found. disable JPEG support.
checking for perl... /usr/bin/perl
checking for Qt... configure: error: Qt (>= Qt 3.2) (headers and libraries) not found. Please check your installation!

blair..

---

### Post by Pablo_Escobar on 2005-11-24
Kdevelop is available in the repositories, no need to compile it.
1. Go to Synaptic Package Manager
2. Search for Kdevelop
3. Install it

(another way is to issue a command in terminal "sudo apt-get install kdevelop")

No need to compile when it's in the repos.

---

### Post by the_it on 2005-11-24
Hello newbie.

Linux, like windows, uses something called a "system path" to determine where all "installed" programs are.  Except that on Linux, installed programs normally are placed in the default path which is usually /usr/bin, but can also be /bin, /sbin/, /usr/sbin/, /usr/local/bin.  Other programs may be placed in /opt, in the user's home directory, or elsewhere.

To access a program that is in the path, simply type its name.  For example, the programs ls, dir, cp, rm, mv, sh and bash are in the path, so you can call them simply by typing their names.  However, if a program is outside the path, you must tell the shell exactly where it is for it to run.  For example, a program called thing is in /home/me/thing, then I can call it by typing /home/me/thing.  I can also just type ./thing if I am currently in /home/me (. stands for the current directory).

Normally, however, installing program in Ubuntu is a quick and easy automatic process, because we use the apt package manager.  You can use the synaptic or adept package manager (which can be found in your system->administrator programs) to browse for and install a large number of linux software.

---

