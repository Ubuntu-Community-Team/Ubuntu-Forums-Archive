---
title: "Powerdevil on Kubuntu Intrepid with KDE 4.2 RC1"
date: 2009-01-26
forum: General Help
---

### Post by TWO on 2009-01-26
I'm currently running Intrepid with KDE 4.2 RC1 and was trying to install Powerdevil yesterday, as I heard that this was going to be the default power management suite for KDE 4.2. However, on trying to install it, Synaptic displayed the message that the program required the package **libplasma2**, whilst I have **libplasma3 **installed, meaning that I was unable to install it. 

Now I know that the KDE 4.2 final release is scheduled for tomorrow, but knowing that releases don't always come on time- like a few days, but I **am **impatient :lolflag:- I was wandering two things:

1) Whether it will be ok to just downgrade to **libplasma2** under KDE 4.2? I'm not really sure what purpose the package serves and how crucial it is to other packages, or if it will break my system.

2) If we can expect a Powerdevil update soon so that it can be used with KDE 4.2?

or

3) If it is actually possible to have it run under the release candidate?

Thanks in advance

TWO

---

### Post by thelner on 2009-01-29
Starting in KDE 4.2, powerdevil is part of the core KDE distro its in the kdebase-workspace-bin package. So you should already have it installed.

Package: kdebase-workspace-bin
Source: kdebase-workspace
Version: 4:4.2.0-0ubuntu1~intrepid1~ppa5
Replaces: kcontrol, kdebase-bin (<< 4:4.0.0-1), kmenuedit, ktip, libplasma2, powerdevil

---

### Post by TWO on 2009-01-30
> **thelner said:**
> Starting in KDE 4.2, powerdevil is part of the core KDE distro its in the kdebase-workspace-bin package. So you should already have it installed.

Package: kdebase-workspace-bin
Source: kdebase-workspace
Version: 4:4.2.0-0ubuntu1~intrepid1~ppa5
Replaces: kcontrol, kdebase-bin (<< 4:4.0.0-1), kmenuedit, ktip, libplasma2, powerdevil

Ah right OK, thanks very much!

---

