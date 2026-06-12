---
title: "help! apt- get help!!!!!!!"
date: 2005-10-19
forum: Desktop Environments
---

### Post by haskan on 2005-10-19
'm using kubuntu . I used apt-get install firestarter but i get this result: 
 
Reading package lists... Done 
Building dependency tree... Done 
E: Couldn't find package firestarter

help needed so much!!

thank you

---

### Post by adwait on 2005-10-19
You need to enable universe in your repositories.Open the /etc/apt/sources.list and add the word universe at the end of the appropriate lines. Take a look at this: [http://www.psychocats.net/sources.html](http://www.psychocats.net/sources.html)

---

### Post by heimo on 2005-10-19
firestarter is in universe - you need to enable it using these instructions:
[http://www.psychocats.net/sources.html](http://www.psychocats.net/sources.html)

Then try to sudo apt-get update or hit Reload in Synaptic package manager and install firestarter. :)

---

### Post by goldenboy on 2005-10-19
You probably have'nt uncommented the universe repository in your /etc/apt/sources.list file.

Uncomment the following lines:

```
# deb [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy universe
# deb-src [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) breezy universe
```

do a

```
sudo apt-get update
```

and then

```
apt-get install firestarter
```

should work as disired

cheers

---

### Post by Pablo_Escobar on 2005-10-19
**sudo** apt-get install firestarter :)

---

