---
title: "Root User"
date: 2006-02-02
forum: Desktop Environments
---

### Post by finalzero on 2006-02-02
Hi,

I noticed Ubuntu hides the root user and only allows a normal user to be created however I would like to have root access as well as I prefer to go in as root user sometimes to adjust something on the system.

I am a seasoned Debian guy which is why I am asking this question :)  Also once I locate the root user details can I change them as per the normal linux/debian method?

Thanks,

Fz

---

### Post by Leif on 2006-02-02
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by deathbyswiftwind on 2006-02-02
to enable the root account you have to enter the following into the terminal
sudo passwd root
that will enable you to make the root password which in turn will enable the root account

---

### Post by finalzero on 2006-02-02
Great,

Thanks for the link (book marked) and info.

Fz

---

### Post by towsonu2003 on 2006-02-02
[QUOTE=deathbyswiftwind]
sudo passwd root
[/QUOTE]
I am seeing this more and more nowadays :) so a quote from the wiki: 
> This is not recommendedand you do not need a root account in Ubuntu. The whole thing is set up to use the sudo command.

---

### Post by aysiu on 2006-02-02
And if you prefer to do things graphically, there are always these options: ```
kdesu konqueror
``` and ```
gksudo nautilus
```

---

### Post by soulestream on 2006-02-02
> I am a seasoned Debian guy which is why I am asking this question

Just not a seasoned forum searcher I guess ;) 

soule

---

