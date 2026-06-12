---
title: "X won't start after kleansweep"
date: 2009-01-18
forum: General Help
---

### Post by Milt15 on 2009-01-18
I used a program called kleensweep to remove the unneeded orphaned files but after reboot x won't start (it appears that there is at least a file whom got deleted was necessary for x ) 
it goes to when it should start but it won't
fsck is right and I have enought free space in the ubuntu partition and my superuser space is 2% (not 5% )

in the recovery mode it can't fix x 
and for dpkg there is a problem for my only internet connection is wireless so if I can connect to it before starting x that would help
iwconfig doesn't show my wireless interface 

any help is appreciated alot

---

### Post by hal8000 on 2009-01-18
To make space. have you tried 

sudo apt-get clean

Back to the problem, kleansweep may have erased these, but backup files of your xorg.conf are kept in /etc/X11 so try

ls /etc/X11xorg*

This will list any copy of xorg.conf so if you see a file called
xorg.conf~

You can type

cp xorg.conf~ xorg.conf

and restart X.

If that fails, regenerate an xorg file with

sudo dpkg-reconfigure xserver-xorg

Hope that helps

---

