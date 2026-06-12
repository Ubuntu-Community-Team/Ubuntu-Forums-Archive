---
title: "How to uninstall macbuntu?"
date: 2011-07-05
forum: Desktop Environments
---

### Post by jeshrel on 2011-07-05
Hi,

i recently installed macbunut in ubuntu 10.10, but when i tries uninstalling it, it is not getting uninstalled. i tried the command
 
 wget [https://downloads.sourceforge.net/project/macbuntu/macbuntu-10.10/v2.3/Macbuntu-10.10.tar.gz](https://downloads.sourceforge.net/project/macbuntu/macbuntu-10.10/v2.3/Macbuntu-10.10.tar.gz) -O /tmp/Macbuntu-10.10.tar.gz
tar xzvf /tmp/Macbuntu-10.10.tar.gz -C /tmp
cd /tmp/Macbuntu-10.10/
./uninstall.sh

but it aint working, the error that occured is shown below in the screenshot kindly help. after installing the file through the terminal i did not change any file location.

---

### Post by BenB1 on 2011-11-14
Same problem in Lucid Lynx. I try to cd to /tmp/Macbuntu-10.04 anf bash tosses back an error. "No such file or directory" So, if the directory does not exist neither does uninstall.sh. 

Tried the Macbuntu theme. It is quite nice. It is also far too much eye candy for me. Please explain how to uninstall it without botching up the computer. Hm, I think I have a back in time back up. :)

Back up restoration did not help. For now, using Clearlooks compact theme, yet still desire removing Macbuntu. Not for me, won't use it, no need keeping it around.

---

### Post by BenB1 on 2011-11-14
Ah ha! Found out how to do it.

From the README file I located via just poking around:

== Uninstall ==

2. How to remove Macbuntu?

2.1 Clicker method

Open Nautilus, then go to your home directory and press Ctrl+H to show hidden files. Go to .macbuntu/10.04-2.2 folder.
After that run the uninstall.sh file as a regular user (not root).
The best way to do that, drag the uninstall.sh file and drop it to opened terminal window.
Press Enter.
Follow the instructions

2.2 Command line method

Open a terminal and type the following commands:

$ cd ~/.macbuntu/10.04-2.2/
$ ./uninstall.sh

or 

$ cd ~/.macbuntu/10.04-2.2/ && ./uninstall.sh

====

Would have been nice had this been given in the instructions on the blog post for installing it. :lolflag: Oh well, at least now we can uninstall it safely, hopefully.

---

