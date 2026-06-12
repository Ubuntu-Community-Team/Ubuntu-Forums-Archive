---
title: "Can someone explain this to me"
date: 2007-04-21
forum: Desktop Effects &amp; Customization
---

### Post by LostArt on 2007-04-21
So in my search for how to install beryl, I've learned two things, 

a. My graphics card is not an ATI mobility Radeon 9100 igp, but a mobility radeon 9200 igp :) 

b. There is a bug with xorg and this card:( 

c. (yes I know that that's three) but I've found this guide, problem is I don't get it, Kinda a noob ;-) so If someone could explain it to me that would be great.

d. (yup this is four) the part I'm stuck at is this I can't even find the directory

"This downloads three files and unpacks the sources into the directory xserver-xorg-driver-ati-version. In this directory is the file src/radeon_bios.c, that we need to edit. Towards the end of this file is a comment saying: 
      
  /* revision 4 has some problem as it appears in RV280,
           comment it off for now, use default instead */"

And after this comment follows a code block that has been commented out. We need to re-enable this code by removind the commenting-out. In my case deleting lines 574 and 561 did the job. 

DVI output with ATI RV280 series graphics cards is broken in xorg. This is caused by a bug in the xorg ati/radeon driver. A solution to the problem is provided by this instruction (requires recompiling the driver). 
Prerequisites
To recompile the driver we need some packages installed on our system. 

$ sudo apt-get install build-essential fakeroot
$ sudo apt-get build-dep xserver-xorg-driver-ati

Instruction
In a new empty directory (our build directory) run: 
$ apt-get source xserver-xorg-driver-ati
This downloads three files and unpacks the sources into the directory xserver-xorg-driver-ati-version. In this directory is the file src/radeon_bios.c, that we need to edit. Towards the end of this file is a comment saying: 
      
  /* revision 4 has some problem as it appears in RV280,
           comment it off for now, use default instead */

And after this comment follows a code block that has been commented out. We need to re-enable this code by removind the commenting-out. In my case deleting lines 574 and 561 did the job. 
Now we can build the driver by running: 

$ dpkg-buildpackage -rfakeroot -uc -b

from within the directory that was created for the package after downloading. 
To install it run: 

sudo dpkg -i xserver-xorg-driver-ati_6.5.7.3-0ubuntu7_i386.deb

from within our build directory. 

Please help me with all of your wisdom.

---

### Post by desheikh on 2007-04-22
you need to know basic linux commands to move around directories and stuff
[http://linuxcommand.org/](http://linuxcommand.org/)
[http://ubuntuforums.org/showthread.php?t=73885](http://ubuntuforums.org/showthread.php?t=73885)
[http://doc.gwos.org/index.php/CommandLineBeginners](http://doc.gwos.org/index.php/CommandLineBeginners)

$ sudo apt-get install build-essential fakeroot
$ sudo apt-get build-dep xserver-xorg-driver-at

after this point fire up a terminal, your starting point is your home directory /home/username
create a directory where youll do you recompiling bit
# mkdir mydirectory

# cd mydirectory

here you run apt-get source xserver-xorg-driver-ati
# gedit src/radeon_bios.c

make the neccessary config changes...

# dpkg-buildpackage -rfakeroot -uc -b

# sudo dpkg -i xserver-xorg-driver-ati_6.5.7.3-0ubuntu7_i386.deb

---

### Post by LostArt on 2007-04-22
Hey thanks for the links, but what do I do after I run

cd my directory

---

