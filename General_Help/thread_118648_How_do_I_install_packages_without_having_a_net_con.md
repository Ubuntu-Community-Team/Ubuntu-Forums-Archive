---
title: "How do I install packages without having a net connection?"
date: 2006-01-17
forum: General Help
---

### Post by Snoopy2052 on 2006-01-17
My computer at home doesn't have a net connection (yet), but yet I'd really rather like to be able to install packages. The concept of not having a net connection seems to be rather alien, though, and I seem to be having tremendous difficulty finding anything out.

What it boils down to is: How do I grab the appropriate files from Universe to save onto a USB stick, then take them home and install them (either with apt-get or (more probably) dpkg)?

Cheers!

---

### Post by kaamos on 2006-01-17
This could help: [http://ubuntuforums.org/showthread.php?t=103404](http://ubuntuforums.org/showthread.php?t=103404)

---

### Post by MacV on 2006-01-17
The main issue i see is finding the right dependancies for the packages you want. Apt will installt the package you want as well as any other required packages along side it, so even if you can get the package you want, you ahve to be very careful about getting the other(if needed) packages assocaiated with it.

---

### Post by Snoopy2052 on 2006-01-17
Excellent! I didn't find that thread when searching a few minutes ago. Thanks for the help, guys!

And yes, I'm aware of `dependency hell', and trying to stay away!

---

### Post by KlausPaiva on 2006-01-17
apt-get has an option for you: -d

This just download the packages, not installing it... Then, you just need to copy the downloaded packages.

---

### Post by Snoopy2052 on 2006-01-17
Nice idea, Klaus, but I'm not on Ubuntu when on the net (only available computers are windows!) so I can't use apt-get either! 

Effectively, I seem to be reduced to cherry-picking my way through the package archives, noting the dependencies of each of them, and grabbing those, and any dependencies *they* may have and so on. It's a pain!

---

### Post by DirtDawg on 2006-01-17
I do the same thing with my main UbuntuBox. This page is my best friend:
[http://packages.ubuntu.com/breezy/](http://packages.ubuntu.com/breezy/)

All packages have links to their dependancies so even if you have to go through a little dependancy hell, at least they're easy to find.

---

### Post by christhemonkey on 2006-01-17
Wish i had had that site! i used ubuntu archives (which doesnt (or didnt) have dependancy links), and spent months running back and forward with my usb pendrive! all that strenous excercise made me think that there must be a better way! so just "borrowed" the modem from my parents windoze machine and used it for myself and synaptic!
I have been to dependency hell and come back (nearly!) unscathed :D

---

