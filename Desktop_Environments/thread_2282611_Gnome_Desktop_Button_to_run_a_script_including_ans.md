---
title: "Gnome Desktop Button to run a script including answer request for username"
date: 2015-06-15
forum: Desktop Environments
---

### Post by Robbyx on 2015-06-15
I have been advised to put the following into a button:

sudo openvpn --config /home/robins/openvpnbook/vpnbook-euro1-udp25000.ovpn


How do I do it?

R

---

### Post by Copper Bezel on 2015-06-15
If you use gksu instead of sudo, it'll give you a graphical prompt. I don't know how nicely that'll play with openvpn. 

Here's [a guide for making a button]("http://askubuntu.com/questions/281293/creating-a-desktop-file-for-a-new-application") for it.

---

