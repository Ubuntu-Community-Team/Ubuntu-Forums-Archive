---
title: "How to find the installed packages"
date: 2009-03-04
forum: General Help
---

### Post by satimis on 2009-03-04
Hi folks,


Ubuntu 8.04 workstation


Just installed 3 packages on repo but forgot their names.  Please advise how to find these last installed 3 packages.


TIA


B.R.
satimis

---

### Post by Lars Stokholm on 2009-03-04
If you used Synaptic, File > History.

---

### Post by satimis on 2009-03-04
> **Lars Stokholm said:**
> If you used Synaptic, File > History.
Hi Lars Stokholm,


Thanks for your advice.  I found them on the history including dependence packages installed.


A further question if without Synaptic Package Manager installed then How to find them?  TIA


B.R.
satimis

---

### Post by albandy on 2009-03-04
dpkg --get-selections

you will see installed for installed applications
and deinstalled for deinstalled applications

---

### Post by satimis on 2009-03-04
> **albandy said:**
> dpkg --get-selections

you will see installed for installed applications
and deinstalled for deinstalled applications
Hi albandy,


The command lists all installed packages, NOT the latest 3 packages installed.


satimis

---

### Post by taurus on 2009-03-04
Look in /var/log/dpkg.log.

```
sudo more /var/log/dpkg.log
```

---

### Post by satimis on 2009-03-04
> **taurus said:**
> Look in /var/log/dpkg.log.

```
sudo more /var/log/dpkg.log
```
Hi taurus,


Thanks for your advice.

But the command can't display the last installed packages precisely.


B.R.
satimis

---

### Post by taurus on 2009-03-04
Post the output of this command from a terminal.

```
sudo tail -23 /var/log/dpkg.log
```

---

### Post by satimis on 2009-03-05
> **taurus said:**
> Post the output of this command from a terminal.

```
sudo tail -23 /var/log/dpkg.log
```
Hi taurus,


The command still can't display the installed packages precisely even increasing the number to -70.  The output includes;```

...  half-installed ...
....  unpacked ....
etc.

```


satimis

---

