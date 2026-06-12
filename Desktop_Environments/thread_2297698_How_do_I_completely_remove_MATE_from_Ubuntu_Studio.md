---
title: "How do I completely remove MATE from Ubuntu Studio?"
date: 2015-10-06
forum: Desktop Environments
---

### Post by yoshii on 2015-10-06
At one point I installed MATE into Ubuntu Studio to test it out and I didn't like it.  
I tried removing it but it didn't remove MATE as a login option and it also didin't remove all the MATE components such as Engrampa Archive Manager.  
How do I get rid of everything from MATE?

---

### Post by NathanRodriguez on 2015-10-06
You could try listing all packages/meta-packages you used in the install and remove them through Synaptic/apt-get, but you risky removing packages essential to your system. I've broken a system of mine doing this with KDE.

---

### Post by egeezer on 2015-10-06
The usual way to remove something completely is (in your case):

```
sudo apt-get purge mate-desktop
```

The use of "purge" rather than  "remove" gets rid of all the extras that came with the initial install.

---

### Post by yoshii on 2015-10-09
thanks guys.  I tried the purge command and it didnt get rid of everthing that mate installed.  .  I guess i will leave them there.  it's just annoying.

---

### Post by vasa1 on 2015-10-09
> **yoshi2 said:**
> ... it didn't remove MATE as a login option ...
Look in /usr/share/xsessions. Don't use a file manager. Use the terminal to see "real" names. Do you see anything MATE-related? You'll need *sudo* to remove the corresponding .desktop file.

```
03:18 PM /usr/share/xsessions $ ll
total 28
drwxr-xr-x   2 root root  4096 Jul 23  2014 ./
drwxr-xr-x 229 root root 12288 Aug 30 07:21 ../
-rw-r--r--   1 root root   385 Nov  1  2013 Lubuntu.desktop
-rw-r--r--   1 root root   238 Nov  1  2013 Lubuntu-Netbook.desktop
-rw-r--r--   1 root root   198 Dec 22  2013 openbox.desktop
03:18 PM /usr/share/xsessions $ 
```

---

### Post by vasa1 on 2015-10-09
> **yoshi2 said:**
> At one point I installed MATE into Ubuntu Studio ...
[LIST]
[*]Which version of Ubuntu Studio, 14.04, 15.04?
[*]Do you remember how you installed MATE? Which command did you use? Or did you use a package manager?
[*]For how long have you had Ubuntu Studio? I ask this because */var/log/apt* saves up to ten log files that could be used to "work backwards".
[*]You could look at [http://cdimage.ubuntu.com/ubuntustudio/releases/vivid/release/ubuntustudio-15.04-dvd-amd64.manifest](http://cdimage.ubuntu.com/ubuntustudio/releases/vivid/release/ubuntustudio-15.04-dvd-amd64.manifest) (or whichever is relevant to you) to know what software is now missing or what software is alien to Ubuntu Studio.
[/LIST]

AFAIK, purging *mate-desktop* will only remove the "metapackage" and not the actual software specified by the metapackage. A nice read on metapackages is here: [http://freedompenguin.com/articles/how-to/what-are-linux-meta-packages/](http://freedompenguin.com/articles/how-to/what-are-linux-meta-packages/)

Bottom line: totally reversing the installation of another desktop environment may not be trivial :(

---

