---
title: "Ndiswrapper without network"
date: 2005-12-24
forum: General Help
---

### Post by faizan on 2005-12-24
Okay.. the story is.. im on vacation and dont have access to a LAN. And i was tryna install KDE which ended in disaster. i had to wipe clean my drive and install ubuntu again. but i dont have a network so i cant install most of the packages i want. wireless is available but i cant get ndiswrapper to work without being on a network. wireless is my only option.
i downloaded the source files from sourceforge and the driver files of my wifi card and burnt them to a cd and then tried installing it on my ubuntu machine. i figured tho that i had no clue as to how this had to be done.

can anyone tell me how to get ndiswrapper to install... what files do i need cause i can burn them from my friends computer.. and then once the files are on my computer... how do i install it??

thanks

---

### Post by emerick7 on 2005-12-24
I had this same problem a few weeks ago when I started up with linux.  This is what I did to get it working:

1. Download the latest ndiswrapper file [here]("http://sourceforge.net/projects/ndiswrapper/")
2. Search and download your windows driver for your wifi (should be filename.INF)
3. Burn onto a CD, then put in your home folder
4. Open up a terminal, then type the following:
- cd /usr/src
- tar xvzf ~/ndiswrapper-1.7.tar.gz
5. Type in sudo -s, and then your password
6. Type ndiswrapper -i /path/to/filename.INF
7. Type ndiswrapper -m
8. Then modprobe ndiswrapper
9. Then type in ndiswrapper -l to see if everything is installed correctly
10. Add 'ndiswrapper' to the end of the modules list by typing gedit /etc/modules
11. Then go into System>Admin>Networking
12. Hopefully, Wireless connection should be there
13. Activate it by following [these directions]("http://flacknews.blogspot.com/2005/11/use-ndiswrapper-to-setup-wireless-in.html") (go down to the pictures to see what you need to fill in)

Hope everything works... post if you have any problems in the process.

---

### Post by az on 2005-12-24
[QUOTE=emerick7]I had this same problem a few weeks ago when I started up with linux.  This is what I did to get it working:

1. Download the latest ndiswrapper file [here]("http://sourceforge.net/projects/ndiswrapper/")
2. Search and download your windows driver for your wifi (should be filename.INF)
3. Burn onto a CD, then put in your home folder
4. Open up a terminal, then type the following:
- cd /usr/src
- tar xvzf ~/ndiswrapper-1.7.tar.gz
5. Type in sudo -s, and then your password
6. Type ndiswrapper -i /path/to/filename.INF
7. Type ndiswrapper -m
8. Then modprobe ndiswrapper
9. Then type in ndiswrapper -l to see if everything is installed correctly
10. Add 'ndiswrapper' to the end of the modules list by typing gedit /etc/modules
11. Then go into System>Admin>Networking
12. Hopefully, Wireless connection should be there
13. Activate it by following [these directions]("http://flacknews.blogspot.com/2005/11/use-ndiswrapper-to-setup-wireless-in.html") (go down to the pictures to see what you need to fill in)

Hope everything works... post if you have any problems in the process.[/QUOTE]


No.  If you download the source, you will have to compile it.

Anyway, you do not need to compile it.  It is on the install cd and the installer cached the ndiswrapper-uitls package on your hard drive.

Just install ndiswrapper-utils using synaptic or any other package manager.

Open a terminal and run

sudo ndiswrapper -i (filename.inf)

(filename.inf is the windows driver for your card -  try the one that came with your card.  If that does not work, visit the manufacturer website for the updated version - sometimes ndiswrapper only works with the very latest version of the windows driver)

Then

sudo modprobe ndiswrapper

If you can configure your wireless card in the networking GUI, you are good to go.  Make the module load on boot by running

sudo gedit /etc/modules
and adding the word "ndiswrapper" at the bottom of the list. Save and exit.

---

### Post by Verbious on 2005-12-24
Try it Azz's way.  ndiswrapper is already installed.  

Go to: System > Administration > Synaptic Package Manager

now search for: ndiswrapper 

mark ndiswrapper-utils for installation and then click apply.

Follow the rest of Azz's instructions.  I just did this myself and I did it the hard way.  Using the built in stuff is much easier.

If for some reason you need the latest ndiswrapper you will have to download and then compile it before you can use it.

---

### Post by emerick7 on 2005-12-24
didn't know it came on the cd... looks like I did it the wrong way.

---

