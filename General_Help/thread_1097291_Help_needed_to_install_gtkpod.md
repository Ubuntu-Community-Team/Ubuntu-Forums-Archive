---
title: "Help needed to install gtkpod"
date: 2009-03-15
forum: General Help
---

### Post by ron999 on 2009-03-15
Hi
I'm using Ubuntu 7.04 Feisty Fawn.
When I try to install **gtkpod** using Synaptic Package Manager I get the following message:-

[B]W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/universe/g/gtkpod/gtkpod_0.99.8-0ubuntu3_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/universe/g/gtkpod/gtkpod_0.99.8-0ubuntu3_i386.deb)
  404 Not Found [IP: 194.169.254.10 80][/B]

How do I fix it?

---

### Post by taurus on 2009-03-15
Feisty has expired and the repos have moved.

[http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)

Therefore, you need to replace **[http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com)** in /etc/apt/sources.list with **[http://old-releases.ubuntu.com](http://old-releases.ubuntu.com)**.

---

### Post by ron999 on 2009-03-15
Thanks for your reply taurus.
My sources list is very confusing for me.
Please will you make the changes.

---

### Post by taurus on 2009-03-15
Okay, make a back up of your current /etc/apt/sources.list.

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.orig
```
Then, edit it

```
gksudo gedit /etc/apt/sources.list
```
and delete _everything_ in there.  Now, paste these lines in.

```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://old-releases.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://old-releases.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://old-releases.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://old-releases.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://old-releases.ubuntu.com /ubuntu/ feisty universe
deb-src http://old-releases.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://old-releases.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://old-releases.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://old-releases.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://old-releases.ubuntu.com/ubuntu feisty-security main restricted
deb http://old-releases.ubuntu.com/ubuntu feisty-security universe
deb-src http://old-releases.ubuntu.com/ubuntu feisty-security universe
deb /http://old-releases.ubuntu.comubuntu feisty-security multiverse
deb-src http://old-releases.ubuntu.com/ubuntu feisty-security multiverse

```
Save it and run then

```
sudo apt-get update
sudo apt-get install gtkpod
```

---

### Post by ron999 on 2009-03-15
Thanks taurus, I've changed that list but when I run the update I get an error:-
ron@ron-desktop:~$ sudo apt-get update
E: Malformed line 17 in source list /etc/apt/sources.list (absolute dist)

---

### Post by taurus on 2009-03-15
There is an extra space between com & /ubuntu/ on line 17.

```
deb http://old-releases.ubuntu.**com/ubuntu**/ feisty universe
```

Also, you need to add / to the second to the last line to separate com & /ubuntu.

```
deb /http://old-releases.ubuntu.com**[COLOR="Blue"]/[/COLOR]**ubuntu feisty-security multiverse
```

---

### Post by ron999 on 2009-03-15
Hi
There's a space on line 17, i've removed it and i'm trying the update again.

---

### Post by ron999 on 2009-03-15
That's done it.
gtkpod is now installed.
Thanks very much:D
Here's a screenshot.

---

### Post by ron999 on 2009-03-15
Screenshot

---

### Post by taurus on 2009-03-15
So everything is back to normal again in Lancashire!

---

### Post by ron999 on 2009-03-15
> **taurus said:**
> So everything is back to normal again in Lancashire!
Yup, I've also amended that next-to-last line as you stated.
:D

---

