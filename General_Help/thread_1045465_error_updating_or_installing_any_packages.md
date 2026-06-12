---
title: "error updating or installing any packages"
date: 2009-01-20
forum: General Help
---

### Post by slade on 2009-01-20
I keep getting an error whenever I update or install anything.  The error is:

```
E: system-tools-backends: subprocess post-installation script returned error exit status 1
```

in an error window, and:

```
Errors were encountered while processing:
 system-tools-backends
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up system-tools-backends (2.6.0-1ubuntu1.1) ...
 * Starting System Tools Backends system-tools-backends
invoke-rc.d: initscript system-tools-backends, action "start" failed.
dpkg: error processing system-tools-backends (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 system-tools-backends
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
```

in a terminal.

the error doesn't seem to effect anything on my system, the software works and I haven't had any problems so far.  but, does anyone know what's going on?

---

### Post by dcstar on 2009-01-20
> **slade said:**
> I keep getting an error whenever I update or install anything.  The error is:

```
E: system-tools-backends: subprocess post-installation script returned error exit status 1
```
.......
the error doesn't seem to effect anything on my system, the software works and I haven't had any problems so far.  but, does anyone know what's going on?

That package did not install correctly, remove it and then reinstall it.

---

### Post by slade on 2009-01-20
> **dcstar said:**
> That package did not install correctly, remove it and then reinstall it.

the problem is, if i try removing it it tries pulling essentially everything with it (ubuntu-desktop and gnome).  I tried a reinstall, with no effect.  is there a way to force it to remove the package without considering dependencies, like the --nodeps option with yum in fedora?  I looked through the man pages for aptitude and apt-get and didn't find anything.

---

### Post by mempman on 2009-01-20
> **slade said:**
> the problem is, if i try removing it it tries pulling essentially everything with it (ubuntu-desktop and gnome).  I tried a reinstall, with no effect.  is there a way to force it to remove the package without considering dependencies, like the --nodeps option with yum in fedora?  I looked through the man pages for aptitude and apt-get and didn't find anything.

I would totally not recommend forcing an uninstall, while ignoring dependencies.  you might want to exhaust all other options first, i.e. try the purge remove command:

apt-get remove --purge package_name

---

### Post by sisco311 on 2009-01-20
try:
```
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
```

---

### Post by slade on 2009-01-20
> **mempman]try the purge remove command:

apt-get remove --purge package_name [/QUOTE]

the problem is, that tries bringing too many packages with it.


[QUOTE=sisco311 said:**
> try:
```
sudo dpkg --configure -a
sudo apt-get -f install
sudo apt-get update
```

```
sudo dpkg --configure -a
Setting up system-tools-backends (2.6.0-1ubuntu1.1) ...
 * Starting System Tools Backends system-tools-backends                         invoke-rc.d: initscript system-tools-backends, action "start" failed.
dpkg: error processing system-tools-backends (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 system-tools-backends
```

---

### Post by amlucent23 on 2009-01-20
I am having the exact same error on my desktop with the exact same package.  Are we sure there wasn't an error/bug with the package at some point (obviously when we both updated)?

I also first attempted to remove the package but it basically attempts to remove Ubuntu when you do!

Any bright ideas?

---

### Post by amlucent23 on 2009-01-21
Bump Bump.. anyone have an idea?  Even if its a long shot I will give it a whirl.

---

### Post by jinbatsu on 2010-01-29
me too... exact the same error.

this is so annoying..
1. I install some application, it installed OK.
2. I remove some application, it removed OK.
3. I update from update manager, it actually update.

but all 3 cases will output at ending with WARNING ERROR:
```
Errors were encountered while processing:
 system-tools-backends
 gnome-system-tools

```

---

### Post by jinbatsu on 2010-01-30
Fixed!!

After I install Ubuntu Tweak, and I ran it.
Application->Package Cleaner->
1. Clean Package
2. Clean Cache
3. Clean Config
4. Clean Kernel

And done!

---

