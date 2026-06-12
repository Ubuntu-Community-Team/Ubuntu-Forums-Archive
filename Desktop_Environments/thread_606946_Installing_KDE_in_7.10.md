---
title: "Installing KDE in 7.10"
date: 2007-11-08
forum: Desktop Environments
---

### Post by bdgenz on 2007-11-08
Installed 710 under Mepis using vmware.

Still not fond of Gnome.

Don't spot any kde in add/remove or synaptics.

Any clues around?

TIA

---

### Post by dabl on 2007-11-08
Installing Kubuntu would be a more straightforward way to get the KDE environment.  With Ubuntu already installed, you can run Synaptic and mark the kubuntu-desktop meta-package for installation. :)

---

### Post by bdgenz on 2007-11-08
> **dabl said:**
> Installing Kubuntu would be a more straightforward way to get the KDE environment.  With Ubuntu already installed, you can run Synaptic and mark the kubuntu-desktop meta-package for installation. :)

If I got any results searching for kde or kubuntu I'd take a stab!

Do I need to add a repo in sources.list, or order up some pixie-dust, or ???

---

### Post by z0phi3l on 2007-11-08
just do this:


```
 sudo apt -get install kubuntu-desktop 
```


from a terminal

---

### Post by bdgenz on 2007-11-08
E: Couldn't find package kubuntu-desktop

Isn't synaptic a gui front end for apt-get?

TIA

---

### Post by lexxonnet on 2007-11-08
hmm... what does your sources.list file look like?
```
cat /etc/apt/sources.list
```

---

### Post by HieroPosche on 2007-11-08
Side note on this, If you add the kubuntu desktop, can you easily revert back to gnome?

I tried KDE a few months ago on a failed Slackware adventure (apparently that's not the greatest distro for  learning linux:)  I'd like to try it again, but I don't want to have to reinstall or totally whipe all my gnome settings.

---

### Post by Whiffle on 2007-11-08
[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

---

### Post by bdgenz on 2007-11-09
> **lexxonnet said:**
> hmm... what does your sources.list file look like?
```
cat /etc/apt/sources.list
```

Mostly remarks like:

# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted

The only repos not remarked:

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

---

### Post by lexxonnet on 2007-11-10
Hmm... try uncommenting all the deb lines and see if it works :)

---

