---
title: "install issues"
date: 2005-12-28
forum: General Help
---

### Post by learning curve on 2005-12-28
How do I install a game that I have downloaded from the internet to my desktop?  Examples are Hatman, Xinvaders and Galaxa for Linux.  I'm kind of lost with the whole install uninstall thing and am very new to Ubuntu.  I know about Advantix and the Sudo apt-get command and using synaptic but I'm lost with the manual install of a program that has been downloaded.  Please help!!:confused:

---

### Post by darth_vector on 2005-12-28
hi,

how did you download the game? do you have a .deb package or the source code for the game? if you have a .deb package then things are really easy:

sudo dpkg -i packagename.deb

if you downloaded the source code then you will have to read the included README file, but you will probably just have to:

./configure
sudo make
sudo make install

in both cases you will have to handle the dependencies before you start.

---

### Post by zoiks on 2005-12-28
A third possibility is you may just have to run a binary program that came with the file(s) you downloaded.  You might have to untar and unzip the program, and run an installer program using ./installer at the command line (replace "installer" with the name of their installer program).  In any case, the website for the program you downloaded should tell you how to install it.

---

### Post by ts. on 2005-12-28
[QUOTE=darth_vector]in both cases you will have to handle the dependencies before you start.[/QUOTE]
If you don't, either dpkg, configure, or make should complain to you at some point anyway and let you know what you're missing.

Another possibility: If you downloaded an .rpm package (that's the format that most other distros use), try downloading the alien utility to convert to .deb, and then use dpkg.

---

