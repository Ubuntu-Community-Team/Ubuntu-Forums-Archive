---
title: "Annoying Update Message + VLC, Movie Player ?'s"
date: 2008-11-22
forum: Desktop Environments
---

### Post by keithld on 2008-11-22
I fixed the annoying update error message by going to Software Sources and "Unchecking" The Installable from CD-ROM/DVD Option...

I got everything working so all is fine with Movie Player & VLC...


Thanks for the help


Seem like a few times a day I get a Yellow Triangle with an Exclamation Mark in it on the top right panel and it tells me to run Update and do a manual check for files... 

What this returns is: **Failed to fetch cdrom:[ubuntu 8.10_intrepid ibex_ -release i386 (20081029.5)]/dists/intrepid/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs**

and 

[B]Failed to fetch cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5)]/dists/intrepid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
[/B]
**Some index files failed to download, they have been ignored, or old ones used instead.**


Anyone know what this means & how to stop the messages?... 

The only thing I remember doing a week ago was to try and get RhythmBox to autorun Audio CD's, I set one of my DVD drives to open with RhythmBox but it doesn't play the music unless I click the play button...


I also Rented Iron Man on DVD from Blockbuster today and neither Movie Player or VLC can read the disk but I can play it in Windows with PowerDVD...  Any ideas?

Hmmm

---

### Post by pietjanjaap on 2008-11-22
I think you installed ubuntu without internet connected, then ubuntu searches on de cd for updates.
So go to "synaptic package manager" change the repositories to the ubuntu server.


After install of ubuntu you have to install codecs etc(windows also can not play dvd's).
The first site is dutch, there you can find what to install after ubuntu install. On the other sites you can also search.(otherwise search on google "howto+ubuntu"


Search forums, ubuntu howto sites etc.

[http://sites.google.com/site/computertip/directdoen](http://sites.google.com/site/computertip/directdoen)
[http://sites.google.com/site/computertip/](http://sites.google.com/site/computertip/)
[http://onlyubuntu.blogspot.com/](http://onlyubuntu.blogspot.com/)
[http://www.ubuntu-unleashed.com/](http://www.ubuntu-unleashed.com/)
[http://www.ubuntu1501.com/](http://www.ubuntu1501.com/)
[http://www.tuxmachines.org/](http://www.tuxmachines.org/)
[http://polishlinux.org/howtos/truecrypt-howto/](http://polishlinux.org/howtos/truecrypt-howto/)
[http://www.ubuntugeek.com/](http://www.ubuntugeek.com/)
[http://ubuntu-tutorials.com/](http://ubuntu-tutorials.com/)
[http://www.ubuntux.org/](http://www.ubuntux.org/)
[http://www.debuntu.org/how-to-instal...lvm-filesystem](http://www.debuntu.org/how-to-instal...lvm-filesystem)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)



[http://www.linuxalt.com/](http://www.linuxalt.com/)
[http://www.openinhoud.nl/zoeken](http://www.openinhoud.nl/zoeken)
[http://www.osalt.com/](http://www.osalt.com/)
[http://linuxappfinder.com/alternatives?page=1](http://linuxappfinder.com/alternatives?page=1)

the best:
[http://damen.dommel.be/Ubuntu.html](http://damen.dommel.be/Ubuntu.html)

the gimp        - very good photoshop
gfslicer        - splitter joiner
peazip         - archiver
hellanzb        - downloaden nzb van usenet
kget            - download program
Inkscape Vector Graphics Editor
Klibido         - to look in usenet groups and nzb download
dvdfab in wine  - the only thing i can't find in linux.
quickpar in wine
k3b writing/burning dvd's
gmount iso       - to mount iso file
KNetLoad Network Monitor - you network activity in a grafic

---

### Post by reddfox321 on 2009-10-13
I've got the same problem. Thought it was just me, but the iron man dvd just will not play. I've reinstalled the gstreamer codecs and nothing. I'm using jaunty by the way.

---

