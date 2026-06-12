---
title: "how to run two synaptics packet managers???"
date: 2009-02-27
forum: General Help
---

### Post by meinvateristnein on 2009-02-27
how do you  run two synaptics packet managers??? if that is pssible i would like to know how

---

### Post by steveneddy on 2009-02-27
I don't think that can be done, and if it could be done, why would you want/need to?

---

### Post by meinvateristnein on 2009-02-27
i need to run like update ans install programs at the same time....... i install at least 2-3 programs and 100 updates a day it would be helpful if i could

---

### Post by entr3p on 2009-02-27
> **steveneddy said:**
> I don't think that can be done, and if it could be done, why would you want/need to?

You're right. If you do try it you will get:
```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

meinvateristnein: What you could do is type this command into the terminal:
```
sudo apt-get install program & sudo apt-get update & sudo apt-get upgrade
```

---

### Post by meinvateristnein on 2009-02-27
cool ......but is there any chance of it messing up while im doing anything??

---

### Post by hikaricore on 2009-02-27
It's not possible to run two package managers at once.
If it were you would likely end up with half installed packages and a corrupted dpkg status file.  (which is essential)

I don't see any reason you can't just be patient and wait for packages to install.  :p

---

### Post by entr3p on 2009-02-28
> **meinvateristnein said:**
> cool ......but is there any chance of it messing up while im doing anything??

Well not really. I'll go over what the code will do because Synaptics is basically a GUI for the commands I just listed.
```
##Install the programs
sudo apt-get install program 

## & <-- basically says "If no errors then go on to the next one"

##This updates your database
sudo apt-get update

##This installs the updates from the database
sudo apt-get upgrade
```

---

### Post by Yellow Pasque on 2009-02-28
> **hikaricore said:**
> I don't see any reason you can't just be patient and wait for packages to install.  :p
NONSENSE. I want to run 100 Package Managers at a time. Tell those lazy Debian/Ubuntu devs to brush up on their spin-locks and mutexes and make dpkg multi-threaded. What am I paying those lazy sons... NVM.

---

