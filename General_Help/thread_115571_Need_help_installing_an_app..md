---
title: "Need help installing an app."
date: 2006-01-10
forum: General Help
---

### Post by fastford on 2006-01-10
Hi

i have ubuntu in a another room of my house and i needed tvtime for it so i downloaded the lastest version onto a disc. Took it to my ubuntu computer extracted it all onto my desktop, now how do i install it. Please remember i dont know how to use ubuntu very well.:confused: 

thanks

---

### Post by mustang on 2006-01-10
Have you tried installing it from Synaptic? It seems to be on the repositories

```
sudo apt-get install tvtime
```

---

### Post by darth_vector on 2006-01-10
this can be done really easily. first enable universe repositories (by uncommenting the relevant lines in /etc/apt/sources.list - it says "uncomment these lines to enable universe). you will have to do this as root
```
sudo gedit /etc/apt/sources.list
```
this will give you access to a whole lot of funky programs. to install the program then do the following
```

sudo apt-get update
sudo apt-get install tvtime
```
and everything is done for you.

if you want to check if a program is available, you can do so by running
```
sudo apt-cache search programname
```

EDIT: too quick ^

---

