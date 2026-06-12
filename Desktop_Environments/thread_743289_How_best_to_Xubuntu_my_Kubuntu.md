---
title: "How best to Xubuntu my Kubuntu?"
date: 2008-04-02
forum: Desktop Environments
---

### Post by kortsen on 2008-04-02
I have Kubuntu Gutsy running perfectly on my computer right now and I would like to try out XFCE and compare it to KDE.  My searching tells me the best way to do it is to install the xubuntu-desktop metapackage.  And the best way to accomplish this and have a clean roll-back if needed is to use aptitude, not apt-get.

Why is there such a difference in what gets installed by the 2 different methods?:confused:

When I try ```
apt-get -s intall xubuntu-desktop
``` there are 275 packages installed.

But when I try ```
aptitude -s install xubuntu-desktop  
``` there are 405 packages to install.:shock:

Let me know if you would like me to post the outputs so you can see the package lists.

---

### Post by mali2297 on 2008-04-02
My guess is that aptitude also installs recommended/suggested packages, see here 
[http://packages.ubuntu.com/gutsy/xubuntu-desktop](http://packages.ubuntu.com/gutsy/xubuntu-desktop)

If you start aptitude interactively, you should be able to find an option to change this behavior.

I would recommend to just install the smaller meta package **xfce4**, but it's up to you how many applications that you want to try out.

---

### Post by kortsen on 2008-04-02
> **mali2297 said:**
> 
If you start aptitude interactively, you should be able to find an option to change this behavior.

I can never find *anything* using aptitude interactively.  But you steered me onto the right track and I found the answer by typing aptitude --help
>   Options:
  
 --with(out)-recommends Specify whether or not to treat recommends as strong dependencies


So the command ```
aptitude -s --without-recommends install xubuntu-desktop   
```wants to install 273 packages.

---

### Post by koshari on 2008-06-23
and how do you intend to roll back, keep a log of the installed packages and then use that for your remove line?

---

### Post by mali2297 on 2008-06-24
> **koshari said:**
> and how do you intend to roll back, keep a log of the installed packages and then use that for your remove line?

If you used aptitude to install xubuntu-desktop, then just type
```
sudo aptitude remove xubuntu-desktop
```

---

### Post by aysiu on 2008-06-24
> **koshari said:**
> and how do you intend to roll back, keep a log of the installed packages and then use that for your remove line?
If you install with *aptitude*, you don't need to. ```
sudo aptitude remove xubuntu-desktop
``` should do the trick.

If you do want to paste in the individual packages, this should help, though:
[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

---

### Post by koshari on 2008-06-27
> If you install with aptitude, you don't need to.

but will it remove things like dolphin ect that are part of the metapackage?

---

### Post by mali2297 on 2008-06-27
> **koshari said:**
> but will it remove things like dolphin ect that are part of the metapackage?

It should remove everything that was installed as a dependency of xubuntu-desktop. *Dolphin* is however a KDE app and not a dependency of xubuntu-desktop.

---

### Post by koshari on 2008-06-29
ok, thunar is what i meant, 

the issue i guess i was trying to ask is how does the installer know if any of the parts of the pakage are dependencies for other things?

---

### Post by mali2297 on 2008-06-30
> **koshari said:**
> ok, thunar is what i meant, 

the issue i guess i was trying to ask is how does the installer know if any of the parts of the pakage are dependencies for other things?

I guess it keeps a log of some kind. 

See the documentation at
[http://algebraicthunk.net/~dburrows/projects/aptitude/doc/en/ch02s02s07.html](http://algebraicthunk.net/~dburrows/projects/aptitude/doc/en/ch02s02s07.html)

---

