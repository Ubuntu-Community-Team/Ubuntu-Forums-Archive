---
title: "Synaptic and Apt dont work anymore"
date: 2005-10-19
forum: Desktop Environments
---

### Post by Patrick on 2005-10-19
Hello guys

Suddeny both of these options dont work anymore.

I tried to install something through Synaptic, but it didnt came up. Tried it with apt-get but no way.

Restarted the machine, same problem...

patrick@ubuntu:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

As a noob i am , i thought, something changed with the right, so i did chown -R patrick /var/lib/apt/lists

But still synaptic wants to start ..... :???:

---

### Post by Ampersand on 2005-10-19
You need to run apt-get with administrator (root) priveleges, ie:

```
sudo apt-get update
```

---

### Post by Patrick on 2005-10-19
[QUOTE=Ampersand]You need to run apt-get with administrator (root) priveleges, ie:

```
sudo apt-get update
```[/QUOTE]

yep i know, the code i showed you was without sudo. Look at this one 

patrick@ubuntu:~$ sudo apt-get update
Password:
patrick@ubuntu:~$

nothing happens, also the same with synaptic

---

### Post by argosreality on 2005-10-19
you need to run the command as: "sudo apt-get update"

---

### Post by argosreality on 2005-10-19
Gah, sorry didn't see that you'd updated the thread. Can you post your /etc/apt/sources.list file?

---

### Post by grj on 2005-10-19
Edit your /etc/apt/sources.list
to include the 2 lines for final release updates.

---

### Post by Patrick on 2005-10-20
When i do sudo apt-get update, i give my pasword and normally it updates the repo's. In my case it doesnt do anything. Also synaptic doesnt start after enterign the pasword. The pasword is correct

---

### Post by migueljacq on 2005-10-20
[QUOTE=Patrick]When i do sudo apt-get update, i give my pasword and normally it updates the repo's. In my case it doesnt do anything. Also synaptic doesnt start after enterign the pasword. The pasword is correct[/QUOTE]

sudo gedit /etc/apt/sources.list

Make sure your sources.list file is the same as what is detailed here:

[http://www.psychocats.net/sources.html](http://www.psychocats.net/sources.html)

in terms of synaptic, dunno, are you trying to enter the root password? because it should only be the user password you have to type. same password as what you logged on with

---

### Post by Patrick on 2005-10-20
[QUOTE=migueljacq]sudo gedit /etc/apt/sources.list

Make sure your sources.list file is the same as what is detailed here:

[http://www.psychocats.net/sources.html](http://www.psychocats.net/sources.html)

in terms of synaptic, dunno, are you trying to enter the root password? because it should only be the user password you have to type. same password as what you logged on with[/QUOTE]

I use that pasword, it worked till yesterday, and suddenly it doesnt work anymore.

---

### Post by Patrick on 2005-10-20
Sorry for the bump, but i cant install nothing with synaptc and apt-get .....:???: 

If it stays like this i need to reinstall

---

