---
title: "source list error"
date: 2006-08-16
forum: Desktop Environments
---

### Post by Magiczero on 2006-08-16
Hi

I am getting this error when I try to run updates.  Help!

The following problems were found on your system:


W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages 
(/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_multiverse_binary-i386_Packages)

What do I do to fix this error?

Thanks

---

### Post by meng on 2006-08-16
Edit the file /etc/apt/sources.list
and comment out the duplicates.

---

### Post by Magiczero on 2006-08-16
How?

---

### Post by repins on 2006-08-16
#From a terminal type in 

```
gedit /etc/apt/sources.list
```

#this will open gedit for you to comment out the duplicates.
comment out the dupplicates by using "#" at the start of the line with out the quotes.

---

### Post by PriceChild on 2006-08-16
> **repins said:**
> #From a terminal type in 

```
gedit /etc/apt/sources.list
``` 
#this will open gedit for you to comment out the duplicates.
comment out the dupplicates by using "#" at the start of the line with out the quotes.

You will need to do this sudoed so you have the rights to edit the file:

```
gksudo gedit /etc/apt/sources.list
```

---

