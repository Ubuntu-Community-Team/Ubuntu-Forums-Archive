---
title: "I've Forgotten How To Install New Software"
date: 2006-06-20
forum: Desktop Environments
---

### Post by Mark76 on 2006-06-20
I've just downloaded Opera 9 and the can't remember the exact incantation to get it from the tar.gz file to a working condition :(

---

### Post by taurus on 2006-06-20
```

cd ~/Desktop
tar xvzf <filename>.tar.gz
cd <filename>
./configure
make
sudo make install

```

---

### Post by givré on 2006-06-20
In a tar.gz file, there is always an INSTALL or/and a README file

---

### Post by Mark76 on 2006-06-20
cd ~/desktop
bash: cd: /home/desktop: No such file or directory

---

### Post by Mark76 on 2006-06-20
I downloaded the files to my home folder. Should I delete them and redownload to another folder?

---

### Post by givré on 2006-06-20
cd ~/Desktop was an exemple, if your .tar.gz is in an other place, cd to this place.
[https://help.ubuntu.com/community/BasicCommands](https://help.ubuntu.com/community/BasicCommands) if you need help for basic commands

EDIT: unix systems are case sensitive, desktop is different than Desktop

---

### Post by mjm115 on 2006-06-20
You shouldn't have to install manually.  Opera is in the repositories.  Take a look at [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/) and [http://ubuntuguide.org/wiki/Dapper#What_packages_do_the_extra_repositories_provide](http://ubuntuguide.org/wiki/Dapper#What_packages_do_the_extra_repositories_provide)

---

### Post by Mark76 on 2006-06-20
Opera 9.0 isn't available in the repository.

What's the file name of it?

---

### Post by Mark76 on 2006-06-20
[QUOTE=givré]In a tar.gz file, there is always an INSTALL or/and a README file[/QUOTE]
There's no Install or Readme file in Opera 9.0

---

### Post by givré on 2006-06-20
```
ls
```to know what is there
did you see the link of my post before? :cool:
Command line are really powerfull, you should take 2 minutes to learn them, especialy if you want to install a tarball

---

### Post by Mark76 on 2006-06-20
Okay. So how do I find out what the file name is?

---

### Post by Mark76 on 2006-06-20
mark-williams@098786weq:~$ apt-get install opera 9.0
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
mark-williams@098786weq:~$

mark-williams@098786weq:~$ apt-get install /home/mark-williams/opera_9.0-20060616.6-shared-qt_en_i386.deb
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
mark-williams@098786weq:~$

---

### Post by givré on 2006-06-20
ok, you were speaking about that kind of filename , sorry :cool: 
As you said before, opera 9 is not in the repo, so you will have to install it manually. 
But from the opera website, you can download .deb made for ubuntu directly. Download it and just double-click on it (if you have dapper)
for breezy, go in a terminal, cd to the good directory and type
```
sudo dpkg -i <filename>
```
and that should be ok

---

### Post by Mark76 on 2006-06-20
sudo dpkg -i.  That's the one :D

---

### Post by Mark76 on 2006-06-20
I tried to install the beta version of Gaim 2.0.0 but I seem to be lacking something called an XML perl parser.  I've looked for it in the repository but came up empty handed.

---

### Post by Mark76 on 2006-06-20
This is what it says

checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool

---

