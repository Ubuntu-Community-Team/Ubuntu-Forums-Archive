---
title: "About software updates and freespace"
date: 2006-07-18
forum: Desktop Environments
---

### Post by mcman42 on 2006-07-18
Greets everyone. Linux is well-known for its fast development, often updates, lots of small and nifty files to help bigger programms run smoothly.

I am pretty sure that every .nix (and ubuntu linux aswell) newbie like me does sometimes install software that is not used later and just takes up prescious hdd space. Is there any software or methods to get rid of unneccessory and unused software and modules that I as a beginner user dont know or forgot of? And the second question, does the update module replaces older packages or adds newer ones? Do we, users, have to clean up older packages some time afterthe newer version is installed(when we are completely sure that newer package works well)  or does the update system does this itself?

Thank you in advance.

---

### Post by Jagot on 2006-07-18
Updates replace packages, not add newer ones.  If new packages become available then you will be able to install them separately.  Not quite sure I understand the first point, but if you've installed software you no longer use then it's up to you to remove it.  If you're talking about stuff installed with Ubuntu by default, Ubuntu doesn't really install much unnecessary software.

---

### Post by mcman42 on 2006-07-19
Ok, thank you, Jagot.

---

### Post by Ramses de Norre on 2006-07-19
You should consider using aptitude instead of apt-get or synaptic, aptitude remembers packages installed as dependency and removes them when the originating program that causes them to be installed is uninstalled.
The syntax is the same as apt-get. (sudo aptitude update && sudo aptitude install package_name)

---

### Post by mcman42 on 2006-07-19
> **Ramses de Norre said:**
> You should consider using aptitude instead of apt-get or synaptic

Hm good point. aptitude doesnt have any gui right?

---

### Post by tseliot on 2006-07-19
> **mcman42 said:**
> Hm good point. aptitude doesnt have any gui right?

It has a GUI.

Type:
```
sudo aptitude
```

---

### Post by Lunar_Lamp on 2006-07-19
Just type in 'aptitude' it's a semi-graphical interface.  (I think the correct term is ncurses?)

---

### Post by mcman42 on 2006-07-19
Sweet.. Thank everyone of you. I found what I was looking for thanks to you guys.

---

### Post by Ramses de Norre on 2006-07-19
I think aptitude's GUI harder to work with than plain commands.. 
But I have only used it twice yet maybe you need to get used to it.

---

### Post by Thund3rstruck on 2006-07-19
Also you probably want to remove package dependencies that are not used by any other package on a regular basis

```

$ sudo aptitude install deborphan
$ sudo aptitude remove -y `deborphan`

```

---

