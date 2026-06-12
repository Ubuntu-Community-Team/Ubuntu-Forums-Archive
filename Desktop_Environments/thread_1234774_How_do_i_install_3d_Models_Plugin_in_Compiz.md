---
title: "How do i install 3d Models Plugin in Compiz???"
date: 2009-08-08
forum: Desktop Environments
---

### Post by zeealpal on 2009-08-08
I just downloaded a compiz 3d model, and i cant use it. The instructions on the forums say goto CCSM --> Effects --> 3D Cube Model. I cant install it. I tried wget and the address, but it said unsupported scheme. Any ideas?

---

### Post by zeealpal on 2009-08-09
DW i found that i hadnt installed unsupported plugins, only main and extra

---

### Post by jtech55 on 2009-09-03
can u say where you got the 3d model plugin and the unsupported? :-(

---

### Post by zeealpal on 2009-09-17
The command is 
sudo apt-get install compiz-fusion-plugins-unsupported

and it adds the pugins tom the compiz config windows.

---

### Post by m374nch0714 on 2010-01-13
> **zeealpal said:**
> The command is 
sudo apt-get install compiz-fusion-plugins-unsupported

and it adds the pugins tom the compiz config windows.

I cant istall it from the command.
It said:
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package compiz-fusion-plugins-unsupported


---

### Post by zororo on 2010-01-13
Install compiz:
```
$ sudo aptitude install compiz
```

Install CompizConfig configurator:
```
$ sudo aptitude install compizconfig-settings-manager

```

Install the Compiz Fusion plugins:

```
$ sudo aptitude install compiz-fusion-plugins-main compiz-fusion-plugins-extra

```

Run the Compiz (Nvidia)

```
$ compiz --replace ccp &
```


and open :popcorn:
```
system -> prefernces ->compizconfig settings manager
```

---

