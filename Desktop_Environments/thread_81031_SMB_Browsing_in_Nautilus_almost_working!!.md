---
title: "SMB Browsing in Nautilus almost working!!"
date: 2005-10-23
forum: Desktop Environments
---

### Post by stwog on 2005-10-23
I installed Breezy yesterday after taking a break from the Linux scene and one thing I noticed was that I was finaly able to browse my windows network though nautilus and even mount my media share!! But things don't seem to be working as they should...

1.) Since this share is for all my music, I would like to be able to add it to my Rhythmbox library, but when I go to add a directory, the share isn't listed while the rest of my drives are. How do I add this music to my library?

2.) When I log in for the first time, the music share icon shows on my desktop, but when I open it I am asked for a password, then when I tell it to remember my password it asks for a "keyring" password. Then for the rest of the session I don't need to enter my password, but if I log out and in again and try to open the share I am asked for my keyring password...  The whole point of saving the password was so that I didn't have to enter a password all the time, but I still have to enter a password to the keyring... How do I  make it so the keyring don't ask for my password?

Thanks for the help guys.

---

### Post by mykey on 2005-10-23
I found it easiest to mount a share - this way it is accessible from any application
make sure you have installed smbfs and smbclient: 
**sudo apt-get install smbfs**
**sudo apt-get install smbclient**
then put the following into a file - make it executable and copy it to e.g. /usr/bin
```
mount -t smbfs //<your server>/<your share> ~/<folder for the share>/ -o credentials=/root/.smbcredentials,dmask=777,fmask=777
```
where <your server> is the IP or name of the machine that is holding the share and <your share> is the share name 
you have to create the <folder for the share> in your homedir
the .smbcredentials file does not have to be hidden or in the root folder - you can put it anywhere you like - it should have the following form
```
username=<user that can access the share>
password=<password of this user>
```
you can call the script directly in a root terminal with <filename> or you can put the following into a file, make it executable and put it in ~/.gnome2/nautilus-scripts/
```
gksudo <filename>
```
this way you can call it from anywhere using the right mouse button

good luck ;)

---

### Post by manicka on 2005-10-23
[http://www.ubuntuforums.org/showthread.php?t=76647&highlight=samba+secure](http://www.ubuntuforums.org/showthread.php?t=76647&highlight=samba+secure)

---

