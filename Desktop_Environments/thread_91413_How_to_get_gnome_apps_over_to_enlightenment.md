---
title: "How to get gnome apps over to enlightenment?"
date: 2005-11-17
forum: Desktop Environments
---

### Post by ch13f121 on 2005-11-17
Hi everyone do you think I can get my old gnome apps (synaptic...gaim etc) over into enlightenment 17?  I can't seem to find a way to do it. Another question I have is about the filesystem stuff on e17, the icons like...combine. and yes I know its beta, but I've never heard of this happening. the icons just layer over each other

---

### Post by Ampersand on 2005-11-17
Would this help?
[http://sourceforge.net/projects/e17genmenu](http://sourceforge.net/projects/e17genmenu)

---

### Post by Paulus on 2005-11-17
Hi!  The way I run gnome/kde apps in enlightenment is to run them from terminal, i.e for synaptic ```
sudo synaptic
```not the best way I guess, not sure how to get the gnome/kde menu, you could try typing gnome-panel in enlighenment, might be a more familiar way of getting some apps up and running.
The best way is to make .eap shortcuts, never done this myself e17 can be scarily unusable sometimes!

[COLOR=Red] EDIT: or just do the above![/COLOR]

---

### Post by ch13f121 on 2005-11-17
ok guys thanks, I'll do that when I get home :D

---

### Post by ch13f121 on 2005-11-17
how do I install genmenu? I can't extract it using dpkg, can someone give me the correct command to extract it and install?

---

### Post by Ampersand on 2005-11-18
You should have a file called 'e17genmenu-4.1.8.tar.gz (or something similar). First you need to extract that (using the archive manager that should open when you double-click on it. Alternatively, you can extract it from the terminal using
```
tar -xvf e17genmenu-4.1.8.tar.gz
```
(use cd to get to the directory where you saved it if it's not in the home folder, and make sure the filename is the same as the one you've got.)

Next, install the tools required to compile it using
```
sudo apt-get install build-essential
```
After that, run the following:
```

cd e17genmenu-4.1.8
./configure
make
sudo make install

```
After that, run 
```

e17genmenu -g

```
(I think) and it'll create icons for your gnome programs in E17.

---

### Post by rado_london on 2005-11-24
This sounds nice but I have a strange problem. When I go to the directory with th sourc code and type 
```
./configure
```
it says: No such file or directory.
I have build-essentials installed.
Any ideas?

---

