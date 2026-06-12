---
title: "Uninstalled DE shows on startup"
date: 2019-03-02
forum: Desktop Environments
---

### Post by cej85 on 2019-03-02
I installed xubuntu-desktop and kde-full but liked neither, so I removed them (remove, purge, autoremove).
Yet when I start my computer the sequence is something like this:

ThinkPad screen
Ubuntu purple
**Xubuntu green with Xubuntu logo**
Ubuntu login screen

That's a bit annoying. Also, Plasma and Xfce Session appear as alternatives when signing in.

xubuntu-desktop and kde-full were uninstalled yet traces remain, how do I get rid of these traces?

Ubuntu 18.04.2 LTS with kernel 4.15.0-45 on x86_64. Thanks in advance.

---

### Post by Dennis N on 2019-03-02
Just removing a package 'xubuntu-desktop' does not remove all the packages that xubuntu-desktop installs. They are still there. xubuntu-desktop is what is called a 'meta package' (a list of other packages) whose purpose is to install those other packages. But it cannot remove them. Those packages can only be removed individually.

Next time, you could be using something like timeshift before you add a new desktop so you can go back to what you had before. Or, if you installed as LVM,  you can use snapshots that can return a system to a previous state.

---

### Post by ajgreeny on 2019-03-02
If you did this recently it may be possible to remove all the packages that xubuntu-desktop and kde-full pulled in with it by looking at the output of command ```
grep -i " install " /var/log/dpkg.log.1 /var/log/dpkg.log
``` Edit that of course for the kde-full install.
Al installed packages will be listed by the date and time; search for xubuntu-desktop to see when you installed it all then you can find everything else that was installed at the same time and remove the whole lot.
It's time consuming but by copying the grep output to a text file then listing everything minus the version info which is not needed you can remove all with a ```
sudo apt purge list of packages
``` command.

---

### Post by cej85 on 2019-03-03
> **Dennis N said:**
> Just removing a package 'xubuntu-desktop' does not remove all the packages that xubuntu-desktop installs. They are still there. xubuntu-desktop is what is called a 'meta package' (a list of other packages) whose purpose is to install those other packages. But it cannot remove them. Those packages can only be removed individually.

Next time, you could be using something like timeshift before you add a new desktop so you can go back to what you had before. Or, if you installed as LVM,  you can use snapshots that can return a system to a previous state.

I see. But, when uninstalling, apt listed a bunch of k* packages that were automatically installed and that could be removed with autoremove, which I applied. Shouldn't that have removed all the extra packages, then?

---

