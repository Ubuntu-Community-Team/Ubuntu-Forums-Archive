---
title: "mp3 plugins"
date: 2006-04-01
forum: Desktop Environments
---

### Post by prisway on 2006-04-01
Hello. I am new here and I have a problem. I have with me the Ubuntu 5.04. Whenever I try to play any mp3 songs, I get an error saying that the plugins for the mp3 aren't installed. How do I go about doing that??

---

### Post by The Captain on 2006-04-02
Hi there
There are many ways, one of the easiest is to use Automatix
i) start a session with Gnome
ii) open up a console
iii) type wget [http://beerorkid.com/automatix/automatix_5.7-3_i386.deb](http://beerorkid.com/automatix/automatix_5.7-3_i386.deb)
iv) type sudo dpkg -i automatix_5.7-3_i386.deb
v) to run Automatix type Automatix in the console

Select what you want to install and you are away

Dave

---

### Post by Sutekh on 2006-04-02
[QUOTE=prisway]Hello. I am new here and I have a problem. I have with me the Ubuntu 5.04. Whenever I try to play any mp3 songs, I get an error saying that the plugins for the mp3 aren't installed. How do I go about doing that??[/QUOTE]
As Automatix is not meant for Ubuntu 5.04 I strongly recommend you should check out this link to help you 

[Ubuntu Wiki - Restricted Formats](wiki.ubuntu.com/RestrictedFormats)

Plus you can learn a little about Ubuntu

You will need to enable the **universe** repository by editing the apt-get sources.list.  Open a Terminal window (Applications -> Accessories) and you can type these commands to get things running.  
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list
```
This code copies the file to a backup and then edits it.  When prompted for a password just use your login password.

In the file look for the lines containing **universe**, like these ones
```
# deb http://archive.ubuntu.com/ubuntu breezy universe
# deb-src http://archive.ubuntu.com/ubuntu breezy universe

```
Just remove the # signs and save.

You can then get the gstreamer0.8-mad package that lets you play mp3s
```
sudo apt-get update
sudo apt-get install gstreamer0.8-mad
```
Then your done!

---

### Post by The Captain on 2006-04-02
There are no problems with Automatix and Breezy.

[http://applications.linux.com/article.pl?sid=06/03/12/209257&tid=47](http://applications.linux.com/article.pl?sid=06/03/12/209257&tid=47)

dave

---

### Post by Sutekh on 2006-04-02
[quote=prisway]I am new here and I have a problem.  I have with me the **Ubuntu 5.04**[/quote]This is not Breezy, its Hoary.  I wouldn't recommend a new user to try out Automatix seeing as it was not meant to be run in Hoary

---

### Post by The Captain on 2006-04-02
[QUOTE=Sutekh]This is not Breezy, its Hoary.  I wouldn't recommend a new user to try out Automatix seeing as it was not meant to be run in Hoary[/QUOTE]


my mistake.

Its just that he posted in the Breezy forum !!!!!!

dave

---

### Post by Sutekh on 2006-04-02
[QUOTE=The Captain]my mistake.

Its just that he posted in the Breezy forum !!!!!!

dave[/QUOTE]
Hey don't sweat it.  I've made that mistake plenty of times.

The Hoary sub-forum isn't as easy to find as the Breezy one, so that's probably why its here.

---

### Post by taekappa on 2006-04-06
i dont have an internet connection at home so how and where can i download codecs to my mp3 player and then what should i do?

---

### Post by Sutekh on 2006-04-06
Without an internet connection its not going to be easy.  There might be another way, but not that I now of.

You can go to the Ubuntu Packages web-page and find a mirror to download the gstreamer0.8-mad package.

[Ubuntu Packages](http://packages.ubuntu.com/)

[Ubuntu Packages - gstreamer0.8-mad](http://packages.ubuntu.com/breezy/libs/gstreamer0.8-mad)

You can get the package from the download section at the bottom.

Now here's the fun bit!

You can install the package by using this command from the folder with the package
```
sudo dpkg -i gstreamer0.8-mad
```
but if there are any unresolved dependencies you will have to download them first and install them.  They are the packages listed on the gstreamer0.8-mad page.

You could end up going around in circles to get all of them installed.  If I get a chance I'll install a fresh install up and find out what you need to install to get it working.  Hopefully there won't be many packages and that some will be on the CD.

---

### Post by prisway on 2006-04-25
Thanks a lot.

---

