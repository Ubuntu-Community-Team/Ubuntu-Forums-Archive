---
title: "Add/Remove No Go"
date: 2007-12-14
forum: Desktop Environments
---

### Post by Lord Darklord on 2007-12-14
Well, I'm pretty new to ubuntu and I just installed 7.10 and I can't use any synaptic to install anything (including terminal). When I click an application in add/remove It just gives me a message saying "The list of applications is not available." and tells me that I have to "reload the list to load it", but when I do, nothing happens. PLEASE HELP!

---

### Post by diatribe on 2007-12-14
check your sources.list

---

### Post by taurus on 2007-12-14
Bet you have all your repos comment out.  Open a terminal and edit /etc/apt/sources.list

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
```
and place a # in front of the first line, cdrom, to comment it out.  Then, remove the # in front of all the lines that start with **deb** & **deb-src**.  Save the changes and run

```
sudo apt-get update
```
Now, you should be able to install whatever you want from Add/Remove.

---

