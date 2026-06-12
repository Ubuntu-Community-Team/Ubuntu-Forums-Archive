---
title: "Help install"
date: 2009-04-07
forum: General Help
---

### Post by mikefoster89 on 2009-04-07
i reboot my machine and the cd is correct but i do not get the langugae menu come up, i get some grub list thing where if i hit tab a list of commands come up its like dos and doesnt seen to have much relveance with ubuntu

thanks in advanced

---

### Post by mrtomservo on 2009-04-07
What version of Ubuntu are you trying to install?  Where did you get the install cd?

---

### Post by mikefoster89 on 2009-04-07
8.10, and i got it form the website from the virgin server on the download list

---

### Post by RedSingularity on 2009-04-07
You sure its not the Ubuntu alternate install cd?  That one uses a command line interface rather than a graphical one.  Its for slower computers.

---

### Post by mikefoster89 on 2009-04-07
i would hazard a guess it is the wrong cd nt the graphical one, where do i get the graphical one from i follwed all the download on the offcial website

---

### Post by RedSingularity on 2009-04-07
Did you try [THIS](http://www.ubuntu.com/getubuntu/download)?

---

### Post by mikefoster89 on 2009-04-07
yeh that is wht i followed all the way through selected the server closest to me and it downloaded the file ubuntu-8.10-desktop-i386.iso

---

### Post by RedSingularity on 2009-04-07
You have the correct one then.  Have you set the CD to boot first in bios?

---

### Post by mikefoster89 on 2009-04-07
its set as one of the things to boot up im nt sure if its first or nt ill check it now and get back to you, thanks for help

---

### Post by mikefoster89 on 2009-04-08
heya m8, yep thats all i had to do was switch the priorities round i think before it was getting some of the invo from the files i had on my harddisk loading something else posss???? but i get the instilation menu up, one thing i was wondering how do you install it to run along side windows so u can slet either one on boot up, just testing then i chose install ubuntu it went hrough the questions and when it got to the partitioner it wanted my whole harddrive i would like to install ubuntu on a seperate partition and run off that is that possible

thanks
:)

---

### Post by RedSingularity on 2009-04-08
Usually it gives you a choice to make a separate partition.  Anyway you can make a linux partition manually with the gParted program in linux.  Just boot the Live CD by picking the "try ubuntu without any changes" option in the menu.  Once you have loaded the desktop environment open a terminal and type "sudo apt-get install gparted".  Once that is done locate the program in your menu and open it.  It has a very easy user interface to follow.

---

### Post by mikefoster89 on 2009-04-08
thanks m8 ill give it a bash

---

### Post by mikefoster89 on 2009-04-08
ok id try tht but now when itry adn boot try ubuntu with no changes or even the install unbuntu it goes to load then comes up with i/o error.......could not boot from cd

argh lol

---

### Post by mikefoster89 on 2009-04-08
SORRY im just using this post to help with another problem, the previous problems have all be fixed:

what's happening now is when i am installing ubuntu i get to the partitioner bit and i do not get the guided other selection it will only let me do the whole drive and i would like to install ubuntu on a partition of my hard drive that has already been made:

my hard drive is partitioned in to 4 bits C: D: E: F: C: has windows on it and i would like to install ubuntu on E: not having the guided selection of selecting a specific partition i went to the manuel option and i selected E: drive but i dnt know what options tht needs to have ntfs etc etc i keep getting a error message saying/////// no root file system is defined

basicaly wht im asking is can i instal ubuntu on a partion of my harddrive and how 

thanks in advanced

XD

---

### Post by RedSingularity on 2009-04-08
Did you try the "Manual" partitioner yet?  I will boot my live CD and take a look at what your seeing.  Maybe i can step you through the manual install.

---

### Post by RedSingularity on 2009-04-08
Oh did you use the Gparted program to make the partitions?

EDIT:  Nevermind it doesnt matter.  You can do it later with the Live CD

---

### Post by mikefoster89 on 2009-04-08
My hard drive is already partitioned it was partitioned when i installed windows ages ago and now i would like to install ubuntu on one of those partitions, the partitioner tht im talking about is the one on the graphical design instilation on ubuntu from the lie cd

---

### Post by RedSingularity on 2009-04-08
Ok good, when you get to the Live CD partitioner do you have an option for a "manual" install?

---

