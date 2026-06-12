---
title: "Quicker Boot Time using Gnome"
date: 2009-05-18
forum: Desktop Environments
---

### Post by ckonestroh on 2009-05-18
First let me say this is not my idea was just browsing the internet looking for ways to make my desktop environment easier to use..


I have been browsing this forum on Desktop enviroment watching the discussions on Docks and which on is the best(about 3 weeks)... Helping other users with common preference problems.... Also been watching videos on ubuntu in Youtube by this user: gotbletu.. He does a great job explaining common problems and how to fix theme 

Anyways I ran accrost this site [http://ubuntu-snippets.blogspot.com/search/label/desktop%20enhancements]("http://ubuntu-snippets.blogspot.com/search/label/desktop%20enhancements")

Explains how to enhance your desktop... Get Gnome to run faster...

Now the effect  I got was a faster boot time by 20 seconds....

Effects I have seen is it moved around my Icons on my Taskbar thats about it haven't noticed any changes or conflicts to desktop environment or programs....

Disable .recently-used.xbel

You should have either .gtkrc or .gtkr in your home directory if not create a new file and add following line to it.

gtk-recent-files-max-age=0 

Now restart your gnome environment for faster desktop environment.

---

