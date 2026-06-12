---
title: "missing terminal in gnome menu"
date: 2010-12-07
forum: Desktop Environments
---

### Post by SmartBits on 2010-12-07
I have managed to setup freeNX server for ubuntu maverick. I am connected using the nomachine nxclient for mac and have a gnome desktop.

I am using the canonical i[mage]("http://uec-images.ubuntu.com/releases/10.10/release/") for the amazon cloud. Its a basic installation.

But, strangely the terminal is missing from the main menu options.

I tried configure it using System > Preferences > Main Menu
But, its not anywhere in the list of options.  

I am not sure if any shortcuts for opening terminal window is working since I am inside a nx client environment.

I am able to ssh and install firefox. And firefox shows up in the menu now. But, am a bit lost how to add terminal to the menu :-)

any help guys ?  


gnome 2.32.0

---

### Post by SmartBits on 2010-12-07
solved.

just added /usr/bin/X11/xterm as a new item.

though it looks barebones and dosen't seem to have themes and such options. Is this a restriction of using NX or is there some other binary ?

---

### Post by mcduck on 2010-12-07
try launching "gnome-terminal" instead of "xterm". It should be included since you are running Gnome.

---

### Post by coffeecat on 2010-12-07
I see from your other thread that you're coming over from Fedora. Welcome! If you were looking for gnome-terminal,  Ubuntu and Fedora put it in different  places in the menu. In Ubuntu you can find it in Applications > Accessories.

---

### Post by SmartBits on 2010-12-07
mmm, I think the problem was gnome-terminal was not installed.
after i installed it using aptitude, I found it under Applications > Accessories

I am a little vague about how NX works. but, looks like one dosent need to have gnome installed on the server side to run a gnome session on the client side ? is that so ?

---

