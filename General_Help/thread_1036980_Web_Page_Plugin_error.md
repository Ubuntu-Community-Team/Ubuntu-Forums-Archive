---
title: "Web Page Plugin error"
date: 2009-01-11
forum: General Help
---

### Post by Nitewalker on 2009-01-11
I am trying to update plugins that are indicated for "Firefox" and it is giving me the following error when I try and install it:

"Can not install 'cacao-oj6-plugin' (E:Unable to correct problems, you have held broken packages.) "

All of the other plugins that were listed installed without error:confused:

---

### Post by hikaricore on 2009-01-11
Try this from a terminal window and let me know what it say:

> sudo apt-get install -f

---

### Post by hikaricore on 2009-01-11
Try this from a terminal window and let me know what it say:

> sudo apt-get install -f

---

### Post by Nitewalker on 2009-01-11
nitewalker@smj:~$ sudo apt-get install -f
[sudo] password for nitewalker: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
nitewalker@smj:~$

---

### Post by Cesaar on 2009-03-08
I'm getting exactly the same error when I try to install the java plugins for firefox
 
this is what i get after entering ```
sudo apt-get install -f 
```

```
cesar@cesar-laptop:~$ sudo apt-get install -f 
[sudo] password for cesar: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  neverball-common libsdl-ttf2.0-0 libmikmod2 libsdl-mixer1.2 libsmpeg0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

