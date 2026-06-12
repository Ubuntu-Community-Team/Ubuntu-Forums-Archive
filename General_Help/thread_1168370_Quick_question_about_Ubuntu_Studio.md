---
title: "Quick question about Ubuntu Studio"
date: 2009-05-24
forum: General Help
---

### Post by ozone_00 on 2009-05-24
I was just wondering if Ubuntu Studio only has multimedia tools, or if it has all (or most) the apps of regular Ubuntu (i.e. web browser, Openoffice.org, etc.  Thanks for the help.

---

### Post by lisati on 2009-05-24
Many of the tools which come preinstalled with "regular" Ubuntu can be installed with Ubuntu Studio.

---

### Post by ozone_00 on 2009-05-24
I assumed at least that much, just wanted to make sure before tried using as my primary OS.

---

### Post by lisati on 2009-05-24
> **ozone_00 said:**
> I assumed at least that much, just wanted to make sure before tried using as my primary OS.

I have Ubuntu Studio on one of my machines, and don't anticipate many (if any) hassles getting the applications you're after.

---

### Post by zobcat on 2009-05-24
You _could_ install ubuntu and then go to synaptic and install ubuntu-studio-desktop. That will give you everthing that comes extra with studio.

---

### Post by ozone_00 on 2009-05-24
Honestly, about 99% of my current Windows usage is web browsing, watching DVDs, listening to mp3s, watching videos (mpg and divX mostly), looking at photos, and using the calculator to balance my checkbook.  I also occasionally burn discs and do some light word processing (nothing for work or school, just personal use) so my non-media editing needs are very basic.

---

### Post by ozone_00 on 2009-05-24
> **zobcat said:**
> You _could_ install ubuntu and then go to synaptic and install ubuntu-studio-desktop. That will give you everthing that comes extra with studio.
I'm new to Linux, please explain.

---

### Post by CatKiller on 2009-05-24
> **ozone_00 said:**
> I'm new to Linux, please explain.

You need to understand the concept of package management.

Linux is just the kernel. A GNU/Linux distribution consists of the kernel and a collection of other software that means that you can actually do useful things with your computer. It's the combinations of this software that distinguishes one distribution from another.

Software is installed as packages. Each package contains the files for that particular piece of software, and a list of other software packages that it depends on to function properly. When you install a software package, you will also automatically install anything else that you need for that software to function. There are also packages, referred to as meta-packages, that don't actually contain any files themselves; they just depend on a list of other packages. So, for example, the ubuntu-desktop package depends on all the things that you would want in a Desktop Ubuntu install, so you can install the full Desktop environment with one simple command.

You could either install Ubuntu Studio and then install the ubuntu-desktop package, or install the normal Ubuntu Desktop and then install the ubuntustudio-desktop package. Either way, you would end up with a system that had the software that was installed with either Ubuntu or Ubuntu Studio. Or you could mix-and-match even more; install Ubuntu, and then install Ardour, Rosegarden and so on, but not the real-time kernel. Or install Ubuntu Studio (which comes with the real-time kernel) and then install OpenOffice.org, Evolution and so on.

The choice of which software you have installed on your computer is completely up to you. The distributions only exist to make the task of getting a particular and common set of software installed simply.

---

### Post by ozone_00 on 2009-05-25
> **CatKiller said:**
> 

You could either install Ubuntu Studio and then install the ubuntu-desktop package, or install the normal Ubuntu Desktop and then install the ubuntustudio-desktop package. 


How does one go about doing this?  Is it done in setup or within Linux?  Not that installing individual programs one by one is a problem, I'm just a lazy mofo :p.

---

### Post by CatKiller on 2009-05-25
> **ozone_00 said:**
> How does one go about doing this?  Is it done in setup or within Linux?  Not that installing individual programs one by one is a problem, I'm just a lazy mofo :p.

With your package manager when you've installed the Operating System. And no, it isn't hard. You open your package manager, find the package you want in the list, select mark for installation and hit Apply. That's it. All the rest gets done automatically.

You probably ought to just try the live cd to see how it works.

---

### Post by satnelav on 2009-05-25
yes, but why kill cats?

---

