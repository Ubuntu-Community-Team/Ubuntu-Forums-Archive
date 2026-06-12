---
title: "synaptic package manager locked"
date: 2007-12-10
forum: Desktop Environments
---

### Post by ggumas on 2007-12-10
when I try to open synaptic package manager I get the error message
"E: The package o3spaces-server needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report."
 how do i resolve this error?
I am limmitted to approaches since synaptic package manager and apt-get are both not fuctioning

George G

---

### Post by taurus on 2007-12-10
What's the exact error message when you run this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo apt-get update
```

---

### Post by ggumas on 2007-12-11
elaborating on my previous message which read
     "when I try to open synaptic package manager I get the error message
      E: The package o3spaces-server needs to be reinstalled, but I can't find an archive for it.
      E: Internal error opening cache (1). Please report."
       how do I resolve this error?
      I am limitted to approaches since synaptic package manager and apt-get are both not functioning"

In addition when I enter 
      apt-get update 
       I do not get an error message and everything seems to work
however If I try to load a package I do get an error message

for example the command
   george@ggubuntu:~$ sudo apt-get install python
returns
   Reading package lists... Done
   Building dependency tree       
   Reading state information... Done
   E: The package o3spaces-server needs to be reinstalled, but I can't find an archive for it.

As a consequence I cannot add any new packages.


George G

---

### Post by guietti on 2007-12-29
I have the same problem: "E:The package o3spaces-server needs to be reinstalled, but I can't find an archive for it.'" 

Paolo

---

