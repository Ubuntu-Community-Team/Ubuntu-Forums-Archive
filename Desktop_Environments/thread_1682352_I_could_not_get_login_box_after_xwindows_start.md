---
title: "I could not get login box after xwindows start"
date: 2011-02-05
forum: Desktop Environments
---

### Post by foretribe on 2011-02-05
I have system problem about my Ubuntu 10.04 system. 
after I boot my Ubuntu, The login box is missing from gnome screen.
I could not login my graphic system. 
I can use the command line by ctrl+alt+f1. I used sudo /etc/init.d/gdm start 
try to restart the xwindows the output is
gdm already started
I try to
stop gdm
start gdm
then the xwindows restarted, but still missing the login box
I also try to use
dpkg-reconfigure xserver-xorg
hoping to re configure the server, but unfortunately there is no change  after I restart the genome, I could still not see the login box
I am confirm that there are additional spaces on my laptop.
I can also enter the graphic system on safe mode by startx command.
Who can help me to solve the problem, let me enter the graphic system

---

### Post by foretribe on 2011-02-07
does any body knows?
or I do not describe the problem clearly

---

### Post by cipherboy_loc on 2011-02-07
The only thing I can think of is try reinstalling GDM:

```

sudo apt-get purge gdm
sudo apt-get install gdm

```


Cipherboy

---

