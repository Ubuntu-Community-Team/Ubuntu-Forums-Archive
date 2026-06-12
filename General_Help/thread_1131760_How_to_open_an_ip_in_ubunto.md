---
title: "How to open an ip in ubunto"
date: 2009-04-21
forum: General Help
---

### Post by mubbashar on 2009-04-21
Like in window we use run and type ip and it open that ip for us but in ubunto how can we do this?????

---

### Post by sahabcse on 2009-04-21
Press alt+f2 and type gnome-terminal. And type ifconfig for find the ip details. For more info pls follow below url

[http://sahabm.blogspot.com/2009/01/linux-network-configuration-ubuntu.html](http://sahabm.blogspot.com/2009/01/linux-network-configuration-ubuntu.html)

---

### Post by mubbashar on 2009-04-21
let you and me connected to lan and your ip adrees is 192.168.1.1 and i want to open ur computer and what i do to open ur computer through run ????

---

### Post by sahabcse on 2009-04-21
Hi

open the terminal and type 

ssh username@192.168.1.1

For installing ssh just run 
#sudo apt-get install ssh

---

### Post by mubbashar on 2009-04-21
it is necessary to write username@ip if i only want to write ip than..

---

### Post by sahabcse on 2009-04-21
Your system username and the remoter username are same means it is not required otherwise we have to give the username. Default shell prompt open in system username.

---

### Post by night_fox on 2009-04-21
In windows when you "open an ip", it takes you to a samba share. If the remote machine is ubuntu, it needs samba to be set up. Go to places and then network, to see peoples samba shares. ssh is the way to log into another machine and run programs on the remote machine, where input/output comes from/goes to the local machine. The remote machine needs an ssh server

---

### Post by mubbashar on 2009-04-21
i do not understand ur mean.

---

