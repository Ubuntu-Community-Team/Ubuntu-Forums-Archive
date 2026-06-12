---
title: "Fedora core 8 and sagem fast 840"
date: 2007-12-23
forum: Fedora/RedHat and derivatives
---

### Post by Arwen on 2007-12-23
Hello everyone!
I installed FC 8 and want to torture myself(:-P) by trying to install sagem fast  840.
Any chances of this happening?
I've found a guide in a forum (it's not in english so no need to paste link),it had the same steps for the installation with those for installation of sagem in ubuntu.
The problem is that when I did > sudo pppd call ueagle-atm it gave me "command not found"
Any suggestions?

Thanx in advance for any help :-)

---

### Post by igknighted on 2007-12-23
there is no sudo  in Fedora, and even if you enable it, it doesn't give you all the commands because many are not in the standard user's path.  Try running it as root by typing 'su -' and entering the root password, then retrying the command.  If this still fails to find the command, try installing pppd via yum.

---

### Post by Arwen on 2007-12-24
I typed > yum install pppd and of course it gave me "could not retrieve mirrorlist etc..
Can I download the package for this command from somewhere so I can put it with a flash stick in my fedora?

---

