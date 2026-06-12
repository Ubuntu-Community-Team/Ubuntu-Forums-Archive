---
title: "Can't install games/programs with multiple discs!!"
date: 2008-09-16
forum: Gaming &amp; Leisure
---

### Post by N00b-un-2 on 2008-09-16
Please help!  I've been trying to install some programs using wine and cedega, both to no avail.  In particular I've been trying to get Need For Speed: Underground 2 installed on my Ubuntu 8.04.1.  when I try to run the install cd in wine, it starts up just fine and begins the installation properly, but then when it gets to the point where it tells me to insert disk 2, when I press the eject button (or manually enter the command wither using the GUI or through the terminal) i get an error message saying that I can't unmount the disk because I am not logged in as ROOT.
With Cedega I have to enter the command "sudo cedega" to get cedega to even load.  If I click on the icon using the GUI, it does the animation like it's going to load the cedega gui but the program never opens.  When I mount the disk and then run install with cedega the program loads just fine and let's me enter my registration key and then promptly closes as soon as the screen to select "typical or custom install" pops up.
I've tried this on both of my computers.
I've also tried making ISOs of the game disks and mounting the images, and the result is exactly the same.  I always get an error message telling me that I have to be logged in as root to unmount the disk/ISO file.  I've tried mounting the ISO files with both Acetone2 and Giso mount but to no avail.  I have the same problem with any other Win based software that incorporates more than one install disk.
PLEASE HELP!!!

---

### Post by Bucky Ball on 2008-09-16
Try doing it through nautilus. Terminal and:

**sudo nautilus**

Will open a gui where you are root.

---

### Post by N00b-un-2 on 2008-09-16
I already tried that too.  And no, you're not ROOT when you use nautilus.  You're just given fulltime super user account access to many but not all system functions.  And SU accounts still don't have full access to everything that ROOT does.  For example, nautilus is unable to access ANYTHING having to do with network settings, or even get on the internet.  I STILL got the same exact message:

unable to unmount /media/cdrom0 
>permissions --you are not logged in as ROOT.  Unable to unmount /media/cdrom0

tried to use the GUI and the terminal while using sudo nautilus command and still no luck.

---

### Post by Bucky Ball on 2008-09-16
[http://www.techzilo.com/how-to-login-as-root-in-ubuntu-8-hardy-heron/](http://www.techzilo.com/how-to-login-as-root-in-ubuntu-8-hardy-heron/)

---

### Post by N00b-un-2 on 2008-09-16
so I figured out how to actually access the root user account (but still unable to log in as root...) go to terminal and enter the command

sudo su -

enter your password and voila! you're now the root user.  I was able to finally get my desktop to install Need For Speed Underground 2 through Cedega and swap disks properly, but not my laptop... (weird, usually my laptop is the one that is less quirky about getting things to work) but now when I try to run the game it keeps telling me that I have the wrong disk in and fails to load the program.

Sigh... I'm sure it will get better eventually, but as for right now Linux gaming just leaves something to be desired.  The games and instant messenger with FULL webcam support are the only things keeping that other partition on my hdd.

---

