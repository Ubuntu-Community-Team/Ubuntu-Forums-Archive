---
title: "Strange Synaptic error"
date: 2006-07-16
forum: Desktop Environments
---

### Post by DavidFL on 2006-07-16
> 
libfaad2-0:
  Depends: libc6 (>=2.3.6-6) but 2.3.6-0ubuntu20 is to be installed


The above occurs when I try to mark libfaad2-0 for installation.  Of course I have the most recent kernel available.

The reason I am trying to install it is because I uninstalled it in order to resolve some aparent conflicts that started occuring.  It was complaining about libfaad2-0 and lame.

What is going on here?  Why does it think 2.3.6-0ubuntu20 is to be installed?

---

### Post by shahramsfamily on 2006-07-27
> **DavidFL said:**
> The above occurs when I try to mark libfaad2-0 for installation.  Of course I have the most recent kernel available.

The reason I am trying to install it is because I uninstalled it in order to resolve some aparent conflicts that started occuring.  It was complaining about libfaad2-0 and lame.

What is going on here?  Why does it think 2.3.6-0ubuntu20 is to be installed?

I am getting the same error.when I try to install qdvdauthor.

Depends: libc6 (>=2.3.6-6) but 2.3.6-0ubuntu20 is to be installed
as well as below messages
  Depends: libgcc1 (>=1:4.1.0) but 1:4.0.3-1ubuntu5 is to be installed
  Depends: libstdc++6 (>=4.1.0) but 4.0.3-1ubuntu5 is to be installed
 Depends: libxine1 (>=1.0.1) but it is not installable

I have the  libc6 2.3.6-0ubuntu20 installed and reinstalled..!

---

### Post by shahramsfamily on 2006-07-27
So many other pages depend on libc6, which I cannot now install.

---

### Post by orlox on 2006-07-27
I believe problems like this occur because the deb packages of ubuntu have the word "ubuntu" added to the package version, so when checking dependencies, some packages require the version without that ubuntu added.

I once managed to install a package that gave this errors by installig the packages it depended on with debian packages. These can be found by a search on google placing "packages.debian.org <package name>". You download it, and then install it by using dpkg as root (sudo dpkg -i <package name>).

However, when trying to install debian packages, they can also conflict with your ubuntu packages, so it can be a very tedious work to fix all those dependencies, and you can end up screwing your system up....

So, I would try to install the packages that cause conflict on your installation from packages.debian.org, and if they fail, Id recommend to search another solution...

---

