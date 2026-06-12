---
title: "Supertux and such"
date: 2005-01-13
forum: Gaming &amp; Leisure
---

### Post by guido48430 on 2005-01-13
Hi I was wondering how to go about installing supertux for ubuntu.  My machine was running redhat 8.0 But I wanted to try something new.  In redhat it's pretty easy with the rpm thing.  Could someone walk me through the process on ubuntu?

thanks in advance :D

---

### Post by garyfitz on 2005-01-13
Use the Synaptic Package Manager (search supertux) install
I am just to dumb, can't find the way put it on the menu
I just goto  /usr/games  and click on supertux to run the program

---

### Post by guido48430 on 2005-01-13
Thanks!  Im assuming synaptic is a package manager that searches the web?

---

### Post by crane on 2005-01-13
synaptic is a package manager the point to repositories designed for warty or hoary unless told other wise. It also points to your install CD.

garyfitz - You should be able to just type supertux in a terminal window to start the program.

You can also create your own shortcut by right clicking on the desktop and selecting create launcher. Just fill in the name and under command enter supertux or   /usr/games/supertux then select an icon. Click OK and your all set! :)

---

### Post by Vulc on 2005-01-13
[QUOTE=guido48430]Hi I was wondering how to go about installing supertux for ubuntu.  My machine was running redhat 8.0 But I wanted to try something new.  In redhat it's pretty easy with the rpm thing.  Could someone walk me through the process on ubuntu?

thanks in advance :D[/QUOTE]


you can also use apt-get if you like the console =)


and if you wanted to install rpms, you have to convert into deb files first using alien, its pretty simple

hope that helps

---

### Post by ldoria on 2005-03-19
I just started to use Ubuntu linux this week and I can´t find a way to download and install supertux and powremanga.

to use synaptic doesn´t work.

Can sombody help me please?

Tks  :lol:

---

### Post by fng on 2005-03-19
First follow these instructions about adding new repositories for apt.
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

then type in a terminal : sudo apt-get install supertux

---

### Post by ldoria on 2005-03-22
Tks a lot. It´s working now. :p

---

