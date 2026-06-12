---
title: "Where do i find Synaptic Package Manager On Debian Lenny"
date: 2008-05-12
forum: Debian
---

### Post by reyhan on 2008-05-12
Hello i just Install Debian LEnny Testing But Where Do i 
Find Synaptic Package Manager?

---

### Post by LaRoza on 2008-05-12
If it has it, try:

```

which synaptic

```

It might not have it (I don't remember if it does, I always use the command line)

---

### Post by jdhore on 2008-05-12
It should be installed by default if you had the installer do the desktop-environment option, and it's under System-Administration-Synaptic...If not,

```
sudo apt-get install synaptic
```

I can guarantee that it is in the Lenny repos

---

### Post by reyhan on 2008-05-12
Ok..... I Just Try this ```
which synaptic
```

And Nothing Happen

And I want to install Synaptic by 
```
apt-get install synaptic
```

this is happen 

> debian:/home/reyhan# sudo apt-get install synaptic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package synaptic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package synaptic has no installation candidate
:confused::confused::confused::confused::confused:

---

### Post by LaRoza on 2008-05-12
> **reyhan said:**
> Ok..... I Just Try this ```
which synaptic
```

And Nothing Happen

And I want to install Synaptic by 
```
apt-get install synaptic
```

this is happen

Post the output of:

```

cat /etc/apt/sources.list

```

It is likely the repositories aren't enabled.

---

### Post by kevCast on 2008-05-12
```
# apt-get update && apt-get install gksu synaptic
```

or, if you use sudo

```
$ sudo apt-get update && apt-get install gksu synaptic
```

---

### Post by doorknob60 on 2008-05-18
Make sure you have the Debian repositories, here's a deb line for ya:
```
deb ftp://ftp.debian.org/debian testing main contrib non-free
```

I'm using debian lenny and earlier today I installed synaptic from those repositories :)

EDIT: don't forget to apt-get update before trying to install

---

### Post by kerry_s on 2008-05-18
in debian if you haven't set up sudo, you need to su:

**su**
type the root password
**apt-get install synaptic**

---

