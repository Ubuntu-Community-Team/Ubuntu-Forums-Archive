---
title: "Dock in edgy"
date: 2007-01-16
forum: Desktop Environments
---

### Post by doerum on 2007-01-16
I've tried to find a good objectdock in [www.gnome-look.org](www.gnome-look.org), but i didn't find any good ones. Does anybody have a tip (whitch one, and how to install it)?

---

### Post by rayraven on 2007-01-16
IF u want an Object Dock styled dock for gnome then u can try engage,
I've been using it and its gr8.

You can install by
adding this repo:
deb [http://edevelop.org/pkg-e/ubuntu](http://edevelop.org/pkg-e/ubuntu) edgy e17

get the key:
wget [http://lut1n.ifrance.com/repo_key.asc](http://lut1n.ifrance.com/repo_key.asc)

add it:
sudo apt-key add repo_key

and doing:
sudo apt-get install engage

Regards...
ray

---

### Post by doerum on 2007-01-17
Thanks Ray!

Regards Dørum

---

### Post by rayraven on 2007-01-17
Also install eutils.
Then add the files u want on dock on the folder

yourhome/.e/e/applications/bar/engage/
Mostly these folders wont be created so if they are not u can create them.

Sorry didnt tell u before.Forgot:) 

Regards,,,
ray

---

### Post by tbeld on 2007-01-18
Can you customize the placement of engage now. I had it installed in 6.06 and couldn't figure out how to control the placement and since I have a dual-head setup, the middle of my big desktop is annoying...

---

### Post by Geekboy on 2007-01-18
How do you start Engage?  :confused:

---

### Post by tbeld on 2007-01-18
I'm guessing you tried this but I would just alt+F2 and type engage.

---

### Post by Geekboy on 2007-01-18
Thanks.

I tried running engage from Terminal and no such luck.  I get the following error.

> engage: error while loading shared libraries: libImlib2.so.1: cannot open shared object file: No such file or directory
Looks like everything did not get installed.  That sucks.

---

### Post by Currahee on 2007-01-19
@Geekboy: you need this package... libimlib2 
If you want to install the 'engage' bar, see this howto: [http://dnnd.netsons.org/archives/2006/12/01/engage-on-ubuntu-edgy-dapper/](http://dnnd.netsons.org/archives/2006/12/01/engage-on-ubuntu-edgy-dapper/)

---

### Post by Danyl on 2007-01-21
> **rayraven said:**
> Also install eutils.
Then add the files u want on dock on the folder

yourhome/.e/e/applications/bar/engage/
Mostly these folders wont be created so if they are not u can create them.

Sorry didnt tell u before.Forgot:) 

Regards,,,
ray

Rayraven, I have installed engage successfully but cannot get icons to appear in the dock.

How do you achieve this? ie drag n' drop (copy) icons from the .icons folder? Help!

---

### Post by chrisg0619 on 2007-01-26
Both dnnd.netsons.org and edevelop.org are down.  Most frustrating.  Any alternate sources for (1) the Edgy howto and (2) the actual Engage sources?

---

### Post by eitan_a on 2007-01-28
i would also like this

---

### Post by Mateo on 2007-01-29
sounds like it's going to be down "for an extended period".

[http://www4.get-e.org/Main/News/_articles/381.html](http://www4.get-e.org/Main/News/_articles/381.html)

---

### Post by Currahee on 2007-01-31
> Both dnnd.netsons.org and edevelop.org are down.
Online again... :D

---

