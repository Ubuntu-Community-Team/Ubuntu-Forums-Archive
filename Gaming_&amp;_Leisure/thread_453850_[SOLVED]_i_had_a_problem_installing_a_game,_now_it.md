---
title: "[SOLVED] i had a problem installing a game, now it has messed me up"
date: 2007-05-24
forum: Gaming &amp; Leisure
---

### Post by k33bz on 2007-05-24
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.

and when i run that command i get this

&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring openttd &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; &#9474;
&#9474; You need to install data files &#9474;
&#9474; &#9474;
&#9474; OpenTTD needs the data files from the original Transport Tycoon Deluxe &#9474;
&#9474; game to run. You should install these data files before you can play the &#9474;
&#9474; game. See README.Debian for more details on which files need to be &#9474;
&#9474; copied where.

how do i get rid of this, i dont have the files for it, so i want to get rid of the installation


and when i try to purge it i get this:


k33bz@treehouse:~$ sudo aptitude purge OpenTTD
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
k33bz@treehouse:~$

---

### Post by hikaricore on 2007-05-24
You havn't by any chance run:

```
sudo dpkg --configure -a
```

Like it told you twice have you?

---

### Post by Sammi on 2007-05-24
Have you tried:
```
sudo aptitude remove OpenTTD
```
?

---

### Post by k33bz on 2007-05-24
nvm, i fixed it

---

### Post by k33bz on 2007-05-24
> **hikaricore said:**
> You havn't by any chance run:

```
sudo dpkg --configure -a
```

Like it told you twice have you?


&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring openttd &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; &#9474;
&#9474; You need to install data files &#9474;
&#9474; &#9474;
&#9474; OpenTTD needs the data files from the original Transport Tycoon Deluxe &#9474;
&#9474; game to run. You should install these data files before you can play the &#9474;
&#9474; game. See README.Debian for more details on which files need to be &#9474;
&#9474; copied where.

where you think that came from

---

### Post by k33bz on 2007-05-24
> **Sammi said:**
> Have you tried:
```
sudo aptitude remove OpenTTD
```
?

nope that didnt do it, gave me same message, i just went in the directory and removed all files associated with the program, thanks though

---

### Post by hikaricore on 2007-05-24
> **k33bz said:**
> &#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring openttd &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
&#9474; &#9474;
&#9474; You need to install data files &#9474;
&#9474; &#9474;
&#9474; OpenTTD needs the data files from the original Transport Tycoon Deluxe &#9474;
&#9474; game to run. You should install these data files before you can play the &#9474;
&#9474; game. See README.Debian for more details on which files need to be &#9474;
&#9474; copied where.

where you think that came from


My guess?  Wyoming.  :D

---

### Post by hikaricore on 2007-05-24
> **k33bz said:**
> nope that didnt do it, gave me same message, i just went in the directory and removed all files associated with the program, thanks though

After that I imagine your packaging system is still broken.. unless you missed telling us a step.

---

### Post by k33bz on 2007-05-24
> **hikaricore said:**
> My guess?  Wyoming.  :D

lol, cute :)

---

### Post by k33bz on 2007-05-24
> **hikaricore said:**
> After that I imagine your packaging system is still broken.. unless you missed telling us a step.

actually it seems to be working fine, i will know when i go and try to install a lib i need.

i try to purge it, no effct, try sudo aptitude remove OpenTTD, with no effect, so i ran whereis OpenTTD, as well as whereis openttd (which most files were under), and then rm them, didnt work at first, but after a few mins my synaptic packet mangaer was back online with no problems, so i dont know

---

### Post by k33bz on 2007-05-24
yep everything seems to be working fine

---

