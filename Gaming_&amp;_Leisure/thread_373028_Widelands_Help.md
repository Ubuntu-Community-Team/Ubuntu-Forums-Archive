---
title: "Widelands Help"
date: 2007-02-28
forum: Gaming &amp; Leisure
---

### Post by Rahano on 2007-02-28
I downloaded the game on the ubuntu, but I cant get it to play with the bianary file.

Can anyone help me?

---

### Post by Perfect Storm on 2007-03-01
please post the output while trying running the binary file from the terminal.

---

### Post by Rahano on 2007-03-01
Ok, when I right click the bianary file in the folder, and click run in terminal,  it loads for a second but nothing happens. Im new to linux, and I dont know how to run it from the terminal itself. It in a folder on my desktop though.

---

### Post by Perfect Storm on 2007-03-01
Well first off, try dragging the binary file to the terminal and hit enter.

---

### Post by Rahano on 2007-03-01
Ok, that worked, but when I hit enter it said

Error while loading shared libraries: libsdl_image 1.2.0 cannot open shared object file.

I realized that I needed the sdl libraries, so I downloaded them, but the archive manager does not recognize, .rpm files, so it doesnt extract.

---

### Post by Perfect Storm on 2007-03-01
You don't need to download stuff from various pages, also .rpm is redhat packages. What you need is A) the terminal to get the package through apt-get/aptitude or B) Use Synaptic package manger

A) Open the terminal and type:
```
sudo aptitude install libsdl-image1.2
```

B) Go to System tab ---> Adminstration ---> Synaptic Pacage Manager.
Use the search button and type libsdl

Most libs and applications can be found through here. You might set up the source list to get even more lib and applications available for you.

---

### Post by Rahano on 2007-03-01
Ok, I followed your directions and either way I cannot find the file, in the terminal I cant find it and in the B) option I cant find it either.

By the way thanks for taking the time to help.
'

---

### Post by Perfect Storm on 2007-03-01
Make sure your sourcelist is set up, here's a good place to do so: 

[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

replace with your current one

```
sudo nano /etc/apt/sources.list
```

Save and exit.

```
sudo aptitude update && sudo aptitude upgrade
sudo aptitude install libsdl-image1.2
```

---

### Post by Rahano on 2007-03-01
My linux system is not connected to the internet, Ive been moving files back and forth with a flash drive, is there anyway to do that without net access?

---

### Post by Perfect Storm on 2007-03-02
You can find them here: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by Rahano on 2007-03-02
Thanks so much, after about a half an hour of installing packages, I got it too work. 

I could kiss you right now, thanks so much.

---

