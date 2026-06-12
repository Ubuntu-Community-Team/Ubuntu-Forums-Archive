---
title: "cannot play music"
date: 2009-05-25
forum: General Help
---

### Post by 54321 on 2009-05-25
How do I get the codecs I need to play music files? Thanks!!!

---

### Post by taurus on 2009-05-25
Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by izizzle on 2009-05-25
They should automatically be downloaded. try updating the system.

---

### Post by 54321 on 2009-05-25
Thanks, but got error:

E: Couldn't find package ubuntu-restricted-extras

---

### Post by taurus on 2009-05-25
Post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

---

### Post by 54321 on 2009-05-25
I cannot seem to get it to paste here. 

But in short: Jaunty main restricted.

---

### Post by taurus on 2009-05-25
Cut the text with the left button of the mouse and paste it here with the middle scroll bar.

---

### Post by 54321 on 2009-05-25
ubuntu@ubuntu:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)]/ jaunty main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jaunty main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jaunty main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jaunty-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jaunty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jaunty universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jaunty universe
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jaunty-updates universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jaunty-updates universe
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jaunty multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jaunty multiverse
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jaunty-updates multiverse
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jaunty-updates multiverse
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security multiverse






ubuntu@ubuntu:~$

---

### Post by ashtone on 2009-05-25
You must uncoment universe and multiverse, I mean you must erase the "#" character before the lines ending with universe or multiverse

This is the way to activate these repos in ubuntu

---

### Post by taurus on 2009-05-25
Go into System -> Administration -> Software Sources and put a check mark on all repos except the last one, Source Code.  Then, remove the check mark for the Cdrom in the window below.  Close it and run

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by 54321 on 2009-05-25
Thanks!! It took awhile, but I played a song!!:popcorn:

---

