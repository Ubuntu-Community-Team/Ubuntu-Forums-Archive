---
title: "Trouble Installing Anything"
date: 2006-08-18
forum: Desktop Environments
---

### Post by Flubs4u on 2006-08-18
I am having trouble installing packages via synaptic or using apt-get.  It all started when I wanted to use Samba to share some files with my windows box.  I went to share a folder in my home directory and Samba gave me the error "Could not apply changes! Fix broken packages first!" So I tried using the 'Fix Broken Packages' option in Synaptic and it said it fixed all the packages but I am still unable to share a folder with Samba.  I saw a few posts on removing a syslink but I was unable to locate anything related to samba in the appropriate directory.  So I figured at this point I would try to just SSH into my box and get the files that way, but when i went into install ssh it wouldn't allow me to do that either.  One more thing worth mentioning is that when I do a sudo apt-get -f install in terminal i get a line back saying "0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded" And I can't help but think this is related.  Any help would be greatly appreciated.

Flubs

---

### Post by ButteBlues on 2006-08-18
$ sudo dpkg --configure -a
$ sudo aptitude update
$ sudo aptitude dist-upgrade

Try that, and then reinstall or fix some of those broken packages, and lmk if it works.

---

### Post by Flubs4u on 2006-08-18
Now when I do a sudo apt-get -f install it says I have 2 packages not updated! Still can't install Samba or SSH...

---

