---
title: "Update manager not working"
date: 2009-04-09
forum: General Help
---

### Post by thadacto on 2009-04-09
Is there a problem with the Ubuntu update for Hardy? Everything is fine until I click "Install" and then nothing happens. A few days ago I managed to update 1 or 2 parts of the update of seven updates. Since then nothing _ it doesn't work. Have I done something or is there a problem at the source end?
No messages - computer doesn't freeze - just nothing happens.

---

### Post by taurus on 2009-04-09
Close down update manager if you have it open.  Then, open a terminal and post the outputs of these two commands, running one at a time.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by thadacto on 2009-04-09
Hi taurus - thanks for coming to my rescue again.

> Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_GB     
Hit [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy Release.gpg
Hit [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy/restricted Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_GB
Hit [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy/main Translation-en_GB
Hit [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy/multiverse Translation-en_GB
Hit [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy/universe Translation-en_GB
Hit [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-updates/restricted Translation-en_GB
Ign [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-updates/main Translation-en_GB
Ign [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-updates/multiverse Translation-en_GB
Ign [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-updates/universe Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Hit [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-proposed Release.gpg
Hit [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-proposed/restricted Translation-en_GB
Hit [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-proposed/main Translation-en_GB
Hit [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-proposed/multiverse Translation-en_GB
Ign [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-proposed/universe Translation-en_GB
Hit [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages   
Hit [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-updates Release
Hit [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-proposed Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages         
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy/main Packages
Hit [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy/restricted Sources
Hit [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy/main Sources
Hit [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy/universe Sources
Hit [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy/universe Packages
Hit [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-updates/multiverse Sources
Hit [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-proposed/restricted Packages
Hit [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-proposed/main Packages
Hit [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-proposed/multiverse Packages
Hit [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-proposed/universe Packages
Hit [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-proposed/restricted Sources
Hit [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-proposed/main Sources
Hit [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-proposed/multiverse Sources
Hit [http://ar.archive.ubuntu.com](http://ar.archive.ubuntu.com) hardy-proposed/universe Sources
Reading package lists... Done
george@george-desktop:~$ 

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  libpq5 linux-headers-2.6.24-23 linux-headers-2.6.24-23-generic
  linux-image-2.6.24-23-generic postgresql-client-8.3
5 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 27.6MB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y

I don't know why it is trying to load or update 2.6.24-23, I have 2.6.24-24 installed.

I haven't continued with "[Y/n]? y" as yet.

---

### Post by thadacto on 2009-04-09
It updated via the terminal.
I'll try the update manager next week and if it fails, I now know how to do it in the terminal.
Thanks taurus.
Thanks gambitt - that link seems to be more about upgrading from hardy to 8.10.

---

