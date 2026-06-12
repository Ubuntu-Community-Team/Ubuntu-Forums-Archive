---
title: "installing new fonts"
date: 2009-01-11
forum: General Help
---

### Post by nateandjennie on 2009-01-11
Hey guys,

I'm still a bit new to all of this, but I'm trying to install some new fonts like arial and times new roman.

I have entered this in the command line

$sudo apt-get install msttcorefonts

but then I get

E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

I have enabled universe and multiverse repositories already.

Can someone explain what this means.

---

### Post by iris-n on 2009-01-11
Hi nateandjennie,

Your problem does seem a bit odd. That error message appears when you're trying to run apt-get install without admin privileges, i. e., as a normal user, instead of root. But the command you typed is perfect, ```
sudo apt-get install msttcorefonts
```
The "sudo" is the command to use root privileges.
Are you able to install any other packages?

Also, try this:```
sudo su
```
and then
```
apt-get install msttcorefonts
```
And post the output.

---

### Post by iris-n on 2009-01-11
Hi nateandjennie,

Your problem does seem a bit odd. This error message appears when you're trying to run apt-get install without admin privileges, i. e., as a normal user, instead of root. But the command you typed is perfect, ```
sudo apt-get install msttcorefonts
```
The "sudo" is the command to use root privileges.
Are you able to install any other packages?

Also, try this:```
sudo su
```
and then
```
apt-get install msttcorefonts
```
And post the output.

---

### Post by nateandjennie on 2009-01-12
I have installed other packages in the past.  I'll update you more after work.  That is if I get a chance to try this.

Thanks for the info though.

Could you please explain the differences between sudo and sudo su?

---

### Post by SuperSonic4 on 2009-01-12
sudo gives you root for just that command whereas sudo su gives you root until you close the terminal window

You can also copy and paste fonts if you have them elsewhere (one line at a time - it may also be easier to use nautilus to copy and paste the fonts [step 3]. To show hidden folders in nautilus press ctrl+H)

```
cd
mkdir ~/.fonts
cp -Rv /path_to_source /.fonts
fc-cache
```

---

### Post by Slim Odds on 2009-01-12
> **nateandjennie said:**
> 
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?


Looks like you have Synaptic running while doing the apt-get. You can only have one package manager running at a time, since it has to lock the package database during the installation.

---

