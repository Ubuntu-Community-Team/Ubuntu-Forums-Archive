---
title: "Trying to install supported Brother printer"
date: 2009-03-20
forum: General Help
---

### Post by mci109 on 2009-03-20
I've tried installing the drivers for my Brother FAX 4100 printer which is supported and I am at an impass.  When I open the package manager I get

E:The package fax4100lpr needs to be reinstalled, but I can't find an archive for it.

How do I fix this.

---

### Post by dcstar on 2009-03-20
> **mci109 said:**
> I've tried installing the drivers for my Brother FAX 4100 printer which is supported and I am at an impass.  When I open the package manager I get

E:The package fax4100lpr needs to be reinstalled, but I can't find an archive for it.

How do I fix this.

What "drivers"?, there are Brother packages in the repositories, you should be using those.

---

### Post by fieroboom on 2009-03-20
More specifically, according to [launchpad](https://launchpad.net/ubuntu/+source/brother-lpr-drivers-laser1/1.0.0-3-0ubuntu4), the driver that supports that printer is:
```
brother-lpr-drivers-laser1
```
and it's in the repos. To install it, just open Synaptic and search for that exact name. It should be the first result; mark it for installation, and apply.
:D
-Paul

---

### Post by mci109 on 2009-03-21
I can't open Synaptic.  I get that message.  What do I need to do to clear that out.

---

### Post by fieroboom on 2009-03-21
> **mci109 said:**
> I can't open Synaptic.  I get that message.  What do I need to do to clear that out.

Oh, I'm sorry, I didn't realize that was a synaptic error. D'oh! Open a terminal (Applications->Accessories->Terminal) and run this:
```
sudo dpkg --purge fax4100lpr
```
If it tells you that it's purging configuration files, then let it finish, and then run this:
```
sudo apt-get install brother-lpr-drivers-laser1
```
Else if the first command gives an error, then copy it and post it here please.
:D
-Paul

---

