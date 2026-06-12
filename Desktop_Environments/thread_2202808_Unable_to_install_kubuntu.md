---
title: "Unable to install kubuntu"
date: 2014-01-31
forum: Desktop Environments
---

### Post by jrmchess on 2014-01-31
When I try to install kubuntu desktop from software centre in unity I get the message "there isn’t a software package called “kubuntu-desktop” in your current software sources". What should I do?

Thanks

---

### Post by sudodus on 2014-01-31
What happens if you run
```

sudo apt-get install kubuntu-desktop
```

from a terminal window? It works in my Ubuntu 12.04 LTS based system.

What version are you running. You can check that with

```
lsb_release -a
```

If you have problems run

```
sudo apt-get update
```
```
sudo apt-get upgrade
```

and try again

---

### Post by jrmchess on 2014-01-31
when I run 
> sudo apt-get install kubuntu-desktop

I get the message: 
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package kubuntu-desktop

So I tried:

> sudo apt-get update
sudo apt-get upgrade
sudo apt-get install kubuntu-desktop

but still getting the same error: > E: Unable to locate package kubuntu-desktop


After running: 
> lsb_release -a

output:
> No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise

---

### Post by sudodus on 2014-01-31
So which version are you running? Please run ```
lsb_release -a
```

---

### Post by howefield on 2014-01-31
If you open up Software Sources, do you have the universe repository selected ?

---

### Post by jrmchess on 2014-01-31
> **sudodus said:**
> So which version are you running? Please run ```
lsb_release -a
```

```
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise
```

---

### Post by jrmchess on 2014-01-31
> **howefield said:**
> If you open up Software Sources, do you have the universe repository selected ?

how do u open Software Sources?

---

### Post by howefield on 2014-01-31
Not sure I remember for 12.04, but try opening the Software Centre and then go to the Edit menu and select Software Sources.

---

### Post by jrmchess on 2014-01-31
> **howefield said:**
> If you open up Software Sources, do you have the universe repository selected ?

> **howefield said:**
> Not sure I remember for 12.04, but try opening the Software Centre and then go to the Edit menu and select Software Sources.

yes it's selected

---

