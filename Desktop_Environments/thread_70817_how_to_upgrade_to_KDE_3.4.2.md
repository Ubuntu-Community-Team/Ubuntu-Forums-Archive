---
title: "how to upgrade to KDE 3.4.2?"
date: 2005-10-01
forum: Desktop Environments
---

### Post by nrwilk on 2005-10-01
Is it possible under Hoary?  I just replaced my breezy install with Hoary, and it fixed lots of bugs.  But I want to install KDE 3.4.2 again.  What packages do I need from synaptic?

I can't run the new beta because I'm on a PPC machine and the beta's only for i386.

Thanks!

---

### Post by Knome_fan on 2005-10-01
Afaik there aren't any 3.4.2 packages for hoary ppc.
There are however 3.4.1 packages.

To install them, simply add ```
deb http://kubuntu.org/hoary-kde341 hoary-updates main
``` to your /etc/apt/sources.list, run apt-get update and then apt-get upgrade.

Hope this helps.

---

### Post by Jackster on 2005-10-01
I'm looking at my sources.list file here and I have an entry which seems to be for KDE 3.4.2:
# KDE 3.4.2
#deb [http://kubuntu.org/hoary-kde342](http://kubuntu.org/hoary-kde342) hoary-updates main

I don't remember adding that :confused:

---

### Post by aysiu on 2005-10-01
[QUOTE=Jackster]I'm looking at my sources.list file here and I have an entry which seems to be for KDE 3.4.2:
# KDE 3.4.2
#deb [http://kubuntu.org/hoary-kde342](http://kubuntu.org/hoary-kde342) hoary-updates main
I don't remember adding that :confused:[/QUOTE] If you have # signs in front of a repository, it won't be used.

---

### Post by nrwilk on 2005-10-04
[QUOTE=Knome_fan]Afaik there aren't any 3.4.2 packages for hoary ppc.
There are however 3.4.1 packages.[/QUOTE]

How do you find this kind of stuff out? Is it mostly just being there when it got released?  Or is it knowing the naming style for the repositories?  Is there a list of repositories somewhere?

---

### Post by Knome_fan on 2005-10-04
[QUOTE=Fealos]How do you find this kind of stuff out? Is it mostly just being there when it got released?  Or is it knowing the naming style for the repositories?  Is there a list of repositories somewhere?[/QUOTE]

It's insider information. ;) 

Seriously, things like this are announced at [www.kubuntu.org](www.kubuntu.org)

---

### Post by nrwilk on 2005-10-04
> **Knome_fan]It's insider information.  said:**
> www.kubuntu.org[/url]

Thanks a lot, Knome_fan!

---

