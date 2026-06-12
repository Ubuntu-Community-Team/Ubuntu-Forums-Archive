---
title: "Login problem"
date: 2013-09-13
forum: Desktop Environments
---

### Post by Ibrahim Mohammed Abdu on 2013-09-13
Hi,
I have install ubuntu 13.04 using usb, about a week ago, everything is working fine. Just of recent i added kubuntu desktop properties, xfce4, gnome classic, gnome failback and cairo desktop and some emerald themes (which i downloaded from gnome art site). everything was functioning normal. Jst today i decided to added Lxdm and edubuntu desktop. some of the packages were downloaded while other were not. 
After shutdown and restarting my system, at the login it shows me Login and some names of other users such as syslog, usb... and saned from then on after typing my username and passwd it will just hang there with the blue screen and a pointer.
 i can only log by pressing ctrl+alt+f2 or f3.....
pls. can anyone help me? pls i need help.

---

### Post by sudodus on 2013-09-13
Maybe it is just too many desktop environments, and some of them are not compatible, so some important file was damaged.

It might be hard to repair, but you can boot from your Ubuntu install CD/DVD/USB drive and ***save your personal files, and re-instal***l Ubuntu after that.

-o-

It is a good idea to try a lot of things and not be afraid, but ***you should have two systems*** (It can be in the same computer, dual boot, or even better if your computer has enough horsepower and memory, a virtual machine. VirtualBox is good software for that.

- One production system, which is stable (I prefer an LTS version, now 12.04)

- One testing system, which you can play with and if it breaks, re-install.

---

### Post by Ibrahim Mohammed Abdu on 2013-09-13
Thanks.
Before i wanted to remove the last package i.e. Lxdm that i install, but whenever i manage to logon using tty all my panels disappear. i tried uninstalling from the synaptic, bt it keep telling me could'nt fetch a package check ur netwk connection.

NB. can't connect my 3G
Thanks

---

### Post by sudodus on 2013-09-13
When you are running in text mode, you can use ***apt-get*** instead of Synaptic. Apt-get is also good in terminal windows, and is often recommended here at the Ubuntu Forums. Run it with superuser privileges, for example

```
 sudo apt-get remove lxdm
``` sudo apt-get remove lxdm

---

