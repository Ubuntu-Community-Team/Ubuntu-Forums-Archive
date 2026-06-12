---
title: "I lost gnome-shell 3 please help"
date: 2011-10-26
forum: Desktop Environments
---

### Post by bahha on 2011-10-26
Hi everybody 
I ve been using  ubuntu 11.10 with Gnome 3.2.0  but when I did and update . 
the software center displays a broken package I tried to repair nothing happens I opened synaptic manager to fix it nothing too . this is what I get when I try to install it via terminal .

> @ubuntu:~$ sudo apt-get install gnome-shell
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gnome-shell : Depends: libecal1.2-10 (>= 3.2.1) but 3.2.0-0ubuntu1 is to be installed
               Depends: libedataserver1.2-15 (>= 3.2.1) but 3.2.0-0ubuntu1 is to be installed
               Depends: libedataserverui-3.0-1 (>= 3.2.1) but 3.2.0-0ubuntu1 is to be installed
E: Unable to correct problems, you have held broken packages.please help

---

### Post by crdlb on 2011-10-26
Much of GNOME 3.2.1 is in oneiric-updates, but some of it, including gnome-shell and evolution-data-server is still in oneiric-proposed. Perhaps you have -proposed enabled for universe (where gnome-shell is) but not -main (where the missing evolution-data-server packages are). I would recommend not using -proposed unless you can't wait for a package in it.

---

### Post by bahha on 2011-10-27
Thank you for answering, but what is the solution ; I'm new to ubuntu !  I'm getting used to it. 
I know some basics and I'm learning some

---

### Post by raja.genupula on 2011-10-27
again open your terminal and type to install gnome-shell...

its going to indicate some unmet things then at that time do this 
 
sudo apt-get install -f

& then again try to install gnome-shell 

all the best.

---

### Post by crdlb on 2011-10-27
The GUI method would be to go to System Settings > Software Sources > Updates. Toggle "Pre-released updates (oneiric-proposed)" at least once, which should make sure it's either fully enabled or disabled. Then update your package lists ('sudo apt-get update') and try again.

If it's still broken, open a terminal and run ```
grep oneiric-proposed /etc/apt/sources.list /etc/apt/sources.list.d/*.list
```
Post the output here.

---

### Post by bahha on 2011-10-27
thank you guys pre-released thing solved the issue . I'm loving ubuntu :)

---

### Post by robbiemacg on 2011-10-27
I'm glad things are up and running smoothly now. I just wanted to ensure that you've added the Gnome3 Team PPA to your sources, so you can continue to get updates, etc. A lot of people seem to have initially installed Gnome Shell via downloaded DEBs.
If you'd like to add the PPA to your sources, you can do so either via the Software Centre or CLI. If you choose to work from the command line, you can just use the following command:

```
sudo add-apt-repository ppa:gnome3-team/gnome3
```

---

