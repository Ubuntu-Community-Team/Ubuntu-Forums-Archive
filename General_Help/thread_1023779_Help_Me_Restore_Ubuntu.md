---
title: "Help Me Restore Ubuntu"
date: 2008-12-28
forum: General Help
---

### Post by DocHolliday2006 on 2008-12-28
Hi. I was having constant crash problems with my computer, so I reformatted and everything was running great. 

So I started reinstalling programs, checking after every one to try to find the one that was causing the crashing. 

I figured out that it was amule, a file sharing program (got it through add/remove programs). It causes the crashing/ slowness of my browser even when it's not running. 

If you install the amule package, it requires that you also remove another  package, but I don't know what that was. I want to uninstall Amule and reinstall the other package. 

Can anyone suggest how I can track down what the removed package was?

---

### Post by taurus on 2008-12-28
Applications -> Accessories -> Terminal
```
sudo apt-get remove amule
```

---

### Post by DocHolliday2006 on 2008-12-28
I just put that in the terminal and it said: 

doc@Zeus:~$ Applications -> Accessories -> Terminal
bash: Applications: command not found
doc@Zeus:~$ 
doc@Zeus:~$ Code:
bash: Code:: command not found
doc@Zeus:~$ ---------
bash: ---------: command not found
doc@Zeus:~$ sudo apt-get remove amule

guess it didn't work. 

Also, I need to put back the package it removed. How do I find what one that was and reinstall it? 
> **taurus said:**
> Applications -> Accessories -> Terminal
```
sudo apt-get remove amule
```

---

### Post by oldos2er on 2008-12-28
"Applications, Accessories, Terminal" isn't a terminal command, it's meant to show what menus in your top panel you use to open a terminal.

 Can you please post the output from the command "sudo apt-get remove amule"?

---

### Post by northern lights on 2008-12-28
> **DocHolliday2006 said:**
> If you install the amule package, it requires that you also remove another  package, but I don't know what that was. I want to uninstall Amule and reinstall the other package. 
Can anyone suggest how I can track down what the removed package was?

```
pille@jox:~$ sudo apt-get install amule
[sudo] password for pille: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  amule-common amule-utils libcrypto++7 libgeoip1 libupnp3 libwxbase2.8-0
  libwxgtk2.8-0
Suggested packages:
  amule-utils-gui geoip-bin
The following NEW packages will be installed:
  amule amule-common amule-utils libcrypto++7 libgeoip1 libupnp3
  libwxbase2.8-0 libwxgtk2.8-0
0 upgraded, 8 newly installed, [COLOR="Red"]0 to remove[/COLOR] and 0 not upgraded.
Need to get 10.5MB of archives.
After this operation, 28.6MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
pille@jox:~$ 

```
As I figured, I can't confirm that installing *amule* would cause the removal of anything else...

---

