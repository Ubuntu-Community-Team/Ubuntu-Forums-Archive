---
title: "Desktop for server 1.10"
date: 2012-04-08
forum: Desktop Environments
---

### Post by toypilot on 2012-04-08
Hi Guys, 

This might be right in front of my face, but I cant see it..

I am pulling my hear out trying to get a desktop GUI for server. Everywhere I look there are instructions for using gnome, but I really want to install unity on server.

I found one site which instructed.. sudo apt-get install unity.

But a reboot returns me to command prompt, and when I type unity I just get a gconf error.

No module named gconf...

I have searched the site for a guide, or instructions.. have searched google and found a guide for unity 5 which also fails.

Any help appreciated...

---

### Post by jerrrys on 2012-04-09
In terminal:

sudo apt-get install --no-install-recommends ubuntu-desktop

Its a 160MB download and will give you unity desktop.

[http://packages.ubuntu.com/oneiric/ubuntu-desktop](http://packages.ubuntu.com/oneiric/ubuntu-desktop)

---

