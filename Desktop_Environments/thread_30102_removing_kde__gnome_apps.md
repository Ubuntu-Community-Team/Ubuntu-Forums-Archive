---
title: "removing kde / gnome apps"
date: 2005-04-27
forum: Desktop Environments
---

### Post by kubuntuuser on 2005-04-27
Hi

I wonder if anyone can help, I would like to remove some of the crap that I dont use with my kubuntu system, I have kde and gnome installed. Please no kde vs gnome battles.

I like apps from each desktop environment and login to both environments from time to time.  However there are apps I dont use eg Evolution, Kontact and there is a lot of duppication in the system tools area. 

If i try to remove Kontact using synaptic. I am warned that 

" Mark additional required changes! The chosen action also affects other packages. The following changes are required  in order to proceed.

To be removed 
   kdepim 
   kubuntu-desktop
"

If I remove kubuntu-desktop wont this remove kde. 

How do I get rid of the junk I dont want

I'd appreciate anyones help


Kubutuuser

---

### Post by heimo on 2005-04-27
I removed something that was in ubuntu-desktop and ubuntu-desktop was removed. But as I didn't explicitly remove ubuntu-desktop, it's dependencies were not removed and Gnome was still there.

In other words... kubuntu-desktop and ubuntu-desktop are metapackages which are there for convenience. It's easier to install one package, which installs the whole desktop, than install all those packages "one-by-one". Removing package that desktop-package depends on, removes that metapackage*, but not all the packages that were installed.. 

Erhm... Ok, it sounds much more comlicated that it is. Yet another way: No. You'll still have KDE. Only those packages that are mentioned, kpim and kubuntu-desktop are to be removed, not kde. If kde would be removed, it would be listed. (Basicly, you'd see lots and lots of packages to be removed.)

*) because it's dependencies are no longer met


EDIT:
 

 [http://packages.ubuntu.com/hoary/misc/kubuntu-desktop]("http://packages.ubuntu.com/hoary/misc/kubuntu-desktop")>   This package depends on all of the packages in the Kubuntu desktop system 

 It is safe to remove this package if some of the desktop system packages are not desired.

   


 
[]("http://packages.ubuntu.com/hoary/misc/kubuntu-desktop")

---

### Post by brk3 on 2005-04-27
Cool thanks for that, was wondering about this before!  :smile:

---

### Post by awtomlinson on 2005-04-27
my question is, if you remove the ubuntu or kubuntu-desktop metapackages, what are the side effects?  i have heard that you will no longer be able to automatically update your system, it must be done manually.  so, does this mean that the new ubuntu update manager would no longer function?

---

### Post by heimo on 2005-04-27
You must be thinking about this:
[http://www.ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=15000 ]("http://www.ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=150002")> 
 This package depends on all of the packages in the Ubuntu desktop system 

 It is safe to remove this package if some of the desktop system packages are not desired. However, it is recommended that you keep it installed, because it is used to carry out certain upgrade transitions (such as adding new packages to the system).  It sounds like at least ubuntu-desktop, and probably kubuntu-desktop packages are used to ... well, define what is included in default desktop. This does not mean that the packages which are already installed, wouldn't be updated. They are.

My guess is that it has been used to update the set of packages which are installed. At this point, where Hoary is in very stable state, this function of this package is minimal. To best of my knowledge. I wouldn't be worried about leaving it out.

---

### Post by kubuntuuser on 2005-04-27
Hello again, 

Thank you all for your resonses.

I am still a little confused, does this mean I will be able to upgrade correctly when the time comes. 

Thanks

KubuntuUser

---

### Post by Seth on 2005-04-27
[QUOTE=kubuntuuser]Hello again, 

Thank you all for your resonses.

I am still a little confused, does this mean I will be able to upgrade correctly when the time comes. 

Thanks

KubuntuUser[/QUOTE]
 All your installed packages would be upgraded, but you might have a problem if new programs are being included as part of the default metapackage. I would suggest just reinstalling the (k)ubuntu-desktop package when the time comes to upgrade and re-removing the stuff you don't want.

---

### Post by heimo on 2005-04-27
[QUOTE=kubuntuuser]
I am still a little confused, does this mean I will be able to upgrade correctly when the time comes. 
KubuntuUser[/QUOTE]

Will your packages be updated when update manager is run? Yes. Can you still use synaptic and kynaptic, yes. Can you later upgrade to next release? Just like everybody else.

What you will not get when kubuntu-desktop or ubuntu-desktop is no longer installed, is changes to the **set** of programs that is included in those packages. This will play no remarkable (or any) role until you decide to upgrade to Breezy Badger (next release of Ubuntu), and even then you get updates.

Only change is that your set of programs for desktop will be more static. This is how I understand this. Even then you can anytime reinstall, or use apt-get to list the packages which would be installed if you decided to reinstall (k)ubuntu-desktop.

It's perfectly fine to not have that package, especially (IMHO) in Hoary, which is now in very stable state (no packages will be added or removed, only security updates to existing packages).

If you still would like to have that package installed, you could probably force to install it even with broken dependencies (missing packages). (with proper flags to apt or dpkg) I just don't see reason for it.

Packages included by [kubuntu-desktop]("http://packages.ubuntu.com/hoary/misc/kubuntu-desktop") and [ubuntu-desktop]("http://packages.ubuntu.com/hoary/base/ubuntu-desktop")

---

### Post by jlstar on 2005-05-13
Ok for **Kubuntu-desktop** package but why **Konqueror** package are removed ?

kind regards

---

