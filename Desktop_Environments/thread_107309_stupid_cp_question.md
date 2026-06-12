---
title: "stupid cp question"
date: 2005-12-22
forum: Desktop Environments
---

### Post by ransomc on 2005-12-22
I'm trying to install ubuntu into this new machine and i've come pretty far, getting over setback after setback, but i'm caught at what would seem to be a very simple task: copying the Nvidia driver pack and binutils tar.gz from a CD to my home directory.

The computer cannot (currently) get internet access and I need the 6100 Nvidia drivers to get X to work.  To instlall the drivers I need binutils, and to install the binutils I need to copy the binutils tar.gz from the CD into the home directory so I can actually compile/work with the files.  And this is where I get stuck.  I've tried the following two things, from the ./cdrom directory:

sudo cp binutils-2.16... ../home

sudo cp binutils-2.16... ../home/ransomc

The first actually acts like it's doing something but after checking the home directory I find nothing. The second is just absurd, as it tells me the directory ../home/ransomc does not exist, even though I can cd ../home/ransomc perfectly fine from the ./cdrom directory.  

I'm somewhat of a linux green so I have no clue what other methods there are to move a file from one place to another (except mv of course, which gives similar results).  Am I missing something very basic here?

---

### Post by kabus on 2005-12-22
try it without the ".." in front of "/home/ransomc".
Or like this :

```
cp binutils-2.16 ~
```

---

### Post by dcstar on 2005-12-22
[QUOTE=ransomc]I'm trying to install ubuntu into this new machine and i've come pretty far, getting over setback after setback, but i'm caught at what would seem to be a very simple task: copying the Nvidia driver pack and binutils tar.gz from a CD to my home directory.
......
sudo cp binutils-2.16... ../home

sudo cp binutils-2.16... ../home/ransomc

The first actually acts like it's doing something but after checking the home directory I find nothing. The second is just absurd, as it tells me the directory ../home/ransomc does not exist, even though I can cd ../home/ransomc perfectly fine from the ./cdrom directory.  

I'm somewhat of a linux green so I have no clue what other methods there are to move a file from one place to another (except mv of course, which gives similar results).  Am I missing something very basic here?[/QUOTE]
Probably, "../" at the start of your file specs means "Use the directory **relative** to where I now am".

Because you could be running this command from anywhere, the destination will be dependant on that "anywhere"!

If you use "/home..... (etc.) it means "Use the **absolute** location "/home..... (whatever)", and this means it doesn't matter where you run the command from.

Try: "sudo cp binutils-2.16... /home" and see if things change.

---

### Post by Sutekh on 2005-12-22
Other issue I can see is that you will need some basic packages to compile the drivers off the cd, and without internet that's not gonna be easy.

---

### Post by ransomc on 2005-12-22
oh wow, yes, the level of my n00bness rose a few notches when

>cp binutils... ~

worked too well.  Thank you.  

And Sutekh, what you foresaw seems to be holding true.  I apparently don't even have gcc or cc so compiling this thing may take a while.  A pity, too.  The machine managed to get online for one installation run and it hasn't been able to connect since.

edit:  Oh and, I just looked at the prerequisites for gcc and one of them is binutils.  Stupid circular logic.  I might just wait till I can get this thing online to fool with it afterall.  Or at least on a compatible graphics card.

---

### Post by Sutekh on 2005-12-22
Well do you have internet access in any way or form?  If you do then it is possible to download the required packages for compiling and then copy them to Ubuntu and install them.

Here's the link;
[http://packages.ubuntu.com/breezy/]("http://packages.ubuntu.com/breezy/")

If you can do this, I'd actually try to use the nvidia packages available from Ubuntu to get your drivers up, rather than try to compile others from source.

---

### Post by dcstar on 2005-12-23
[QUOTE=ransomc]
.......
edit:  Oh and, I just looked at the prerequisites for gcc and one of them is binutils.  Stupid circular logic.  I might just wait till I can get this thing online to fool with it afterall.  Or at least on a compatible graphics card.[/QUOTE]
You should be able to re-install with the basic VESA video driver selected, and then get it going with the full graphics functionality sorted out later.

---

### Post by ShirishAg75 on 2005-12-23
Sorry for hijacking the thread but have a similar question, how do I copy the /etc directory with all the sub-directories  to let's say /media/G/etc a directory I made so that the all the contents are copied. I just wanna backup /etc. 
      I searched the cp man & tried 
```
cp -r (for recursively) /etc /media/G/etc
``` this resulted only in the files being copied & not the directories. Thanx in advance.

---

### Post by kabus on 2005-12-23
[QUOTE=shirishag75]Sorry for hijacking the thread but have a similar question, how do I copy the /etc directory with all the sub-directories  to let's say /media/G/etc a directory I made so that the all the contents are copied. I just wanna backup /etc. 
      I searched the cp man & tried 
```
cp -r (for recursively) /etc /media/G/etc
``` this resulted only in the files being copied & not the directories. Thanx in adcvance.[/QUOTE]

try 

cp -a /etc /media/G

---

### Post by ShirishAg75 on 2005-12-23
well it did the trick but was giving errors such ```
 cp: cannot create symbolic link `/media/G/etc/alternatives/lupdate.1.gz': Operation not permitted
```.

---

### Post by ransomc on 2005-12-25
Well, it took a couple of days because I insisted on not using a GUI to learn my way around the ubuntu file system/shell commands (the package list was very helpful).  I finally broke down and used VESA to remove some kernel packages that were getting in the way, as described by tseliot's [guide]("http://ubuntuforums.org/showthread.php?t=75074"), and all in all it was a great way to get into the culture searching through threads for answers and learning how to transfer/unpack files.

Now that the 6100 works, I'm moving on to the network card.  

Thank's everyone for your help and Merry Christmas! (or Happy Hanukah or Happy Kwanza or just good health if you prefer)

---

