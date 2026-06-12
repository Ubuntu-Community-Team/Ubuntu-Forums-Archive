---
title: "New Install: Need Help"
date: 2009-03-21
forum: General Help
---

### Post by maxjet on 2009-03-21
Hi,

My first post and my first problem. I have just installed Ubuntu Server on an old dell machine. I followed the prompts pretty easily and its all installed and now on its first boot.

It asked me for my user name and password which is fine and now stuck with the following line:

user@ubuntu-email:~$

how do i get into the GUI part from here?

Help im an absolute novice on a project to see if i can learn a system by just the forums and testing!

---

### Post by taurus on 2009-03-21
That is what you get, commandline, if you installed the server version.  If you want to have Gnome desktop environment, you now need to install it.

```
sudo apt-get update
sudo apt-get install ubuntu-desktop gdm
sudo /etc/init.d/gdm start
```

p.s.  The desktop CD (LiveCD) would install all of that for you.  How much RAM does it have anyway?

---

### Post by hyper_ch on 2009-03-21
why did you install the server?

---

### Post by maxjet on 2009-03-21
Installed server to try to setup an email server with an alternative to exchange. Ive learnt MS and Mac OS's now trying Linux. Everything i know ive done without classes and books so its just a test really to see if i can do it.

---

### Post by maxjet on 2009-03-21
Got 2gb ram and an intel dual core processor. 250gb hdd in an old dell case (9150 i think!)

---

### Post by hyper_ch on 2009-03-21
have a look at the perfect server setups over at [http://www.howtoforge.com](http://www.howtoforge.com)

and linux servers are usually run headless - that means no gui - as none is needed and as it is encourged to use none.

---

### Post by Klaz168 on 2009-03-21
That's fine, because you did not install the Desktop version.
Server CD does NOT come with any GUI.

---

### Post by maxjet on 2009-03-21
> **taurus said:**
> That is what you get, commandline, if you installed the server version.  If you want to have Gnome desktop environment, you now need to install it.

```
sudo apt-get update
sudo apt-get install ubuntu-desktop gdm
sudo /etc/init.d/gdm start
```

p.s.  The desktop CD (LiveCD) would install all of that for you.  How much RAM does it have anyway?

OK got that sorted. WIll it boot to this everytime now?

---

### Post by maxjet on 2009-03-21
Got a new problem now...

It keeps crashing! A little bit of use after being logged in and it just stops responding.

Any help on how to find out whats causing it?

---

