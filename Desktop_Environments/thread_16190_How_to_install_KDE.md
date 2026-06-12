---
title: "How to install KDE?"
date: 2005-02-19
forum: Desktop Environments
---

### Post by dogandacomputer on 2005-02-19
Simple question, hope there is just as simple an answer. How do I install KDE? Can I install it with GNOME being installed? Is it possible to have KDE and GNOME on the same machine? Can you tell I am a Linux newbie?

---

### Post by Xian on 2005-02-19
Sure, you can run both of those environments on the same machine. You just need to read in the *Starter Guide* [How To Add Extra Repos](http://ubuntuguide.org/#extrarepositories), and then open a terminal and issue the command: 

sudo apt-get install kde

---

### Post by bored2k on 2005-02-20
[QUOTE=Xian]Sure, you can run both of those environments on the same machine. You just need to read in the *Starter Guide* [How To Add Extra Repos](http://ubuntuguide.org/#extrarepositories), and then open a terminal and issue the command: 

sudo apt-get install kde[/QUOTE]

This is uber easy
in terminal type
$sudo su
#gedit

this will bring the text editor, open /etc/apt/sources.list
and add ur debian sources, here are some:


after u add these, save the text and back in terminal [still as sudo root[
#apt-get update
after thats done
#apt-get install kde




OR , open synaptic and skip all the learning from above  :-x

---

