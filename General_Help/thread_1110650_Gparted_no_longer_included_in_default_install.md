---
title: "Gparted no longer included in default install?"
date: 2009-03-30
forum: General Help
---

### Post by jasontan6 on 2009-03-30
Apologies if this has been posted before.

Why isn't GParted included with a default installation of ubuntu since Hardy (? I don't know which release, seems quite a long time ago) It's a little annoying because I don't have internet access on the box i installed ubuntu on to fix Windows.

Thanks in advance.

---

### Post by DGortze380 on 2009-03-30
> **jasontan6 said:**
> Apologies if this has been posted before.

Why isn't GParted included with a default installation of ubuntu since Hardy (? I don't know which release, seems quite a long time ago) It's a little annoying because I don't have internet access on the box i installed ubuntu on to fix Windows.

Thanks in advance.

It has been installed by default in LONG time, not sure if it ever has been actually..

You don't need internet access, put your Ubuntu LiveCD in (while booted to your install ... ie. don't boot the LiveCD). 

```

sudo apt-get install gparted

```

---

### Post by Cybie257 on 2009-03-30
> **jasontan6 said:**
> Apologies if this has been posted before.

Why isn't GParted included with a default installation of ubuntu since Hardy (? I don't know which release, seems quite a long time ago) It's a little annoying because I don't have internet access on the box i installed ubuntu on to fix Windows.

Thanks in advance.

I've noticed that myself as it's on the Live version, yet not in the installed version. One thing that might work since you don't have the machine on the net is to use the install CD as the package source. It does exist on the CD, but I must admit, I've never tried that before. Looking at the "software sources" options, there is a box "Installable from CD-ROM/DVD" box where you can check the option box to include that as a source. I'm thinking that you might be able to install it from the CD?? Maybe someone else can expand on that with experience.

-Cybie

EDIT: See the above post that was posted while I was writing this reply. lol. I thought it was able to be done and there's how. :)

---

### Post by jasontan6 on 2009-03-30
Thanks for speedy replies.  I'm not sure about installing using apt-get though... :confused: I think I browsed the live cd using Synaptic before and i didn't find gparted in it... oh well guess I'll have to try again to be sure.

Thanks a lot again.

---

### Post by dcstar on 2009-03-30
> **Cybie257 said:**
> I've noticed that myself as it's on the Live version, yet not in the installed version. One thing that might work since you don't have the machine on the net is to use the install CD as the package source. It does exist on the CD, but I must admit, I've never tried that before. Looking at the "software sources" options, there is a box "Installable from CD-ROM/DVD" box where you can check the option box to include that as a source. I'm thinking that you might be able to install it from the CD?? Maybe someone else can expand on that with experience.


There is only so much that can fit on one CD and also what is appropriate for the setup phase and actual post-install phase, that is why decisions are made as to what apps to have installed initially and what to leave out.

---

### Post by CatKiller on 2009-03-30
For most users, GParted is only useful on the install disk. Once Ubuntu is actually installed, there's not that much point having GParted installed, since you can't change any of your Ubuntu partitions anyway (since they're mounted to let you actually run GParted).

As others have pointed out, you can always use GParted from the install disk to make any changes that you want (which you'd need to do anyway if you wanted to change any of your Ubuntu partitions) or use the install disk as a repository for Synaptic or apt-get. If you put the cd in, you'll get a prompt asking you if Ubuntu should use the cd as a repository.

---

