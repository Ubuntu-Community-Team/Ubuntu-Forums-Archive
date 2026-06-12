---
title: "Gnome 2 in Ubuntu 11.10 does not save panel changes"
date: 2012-02-15
forum: Desktop Environments
---

### Post by chrarnold on 2012-02-15
Hi,

I am new to this forum, and I did not find any posts that are related to my topic, so I would appreciate any help for the following issue.

I installed a fresh Ubuntu 11.10, which works like a charm. I switched back to the old Gnome (fallback mode), which also worked at the beginning. However, after installing some packages (I don't know when exactly the issue occurred), I now have the following issues:

1) The Gnome panels do not save any changes, if I reboot, all the changes I made are lost, which is extremely frustrating. For example, adding panels or items, or shortcuts to the panel are lost.
2) In particular, the panel at the bottom does not contain any items, and I always have to add the "Window List" in order to see the open windows.

I already tried various things to fix that:
1) Remove the gnome-shell package, and reinstall them using apt-get. Similarly, sudo apt-get -o DPkg::options::=--force-confnew --reinstall install gnome-shell doesn't help either.
2) The only potentially useful log message I find is in syslog (grep gnome *): 
gnome-session[1787]: WARNING: Unable to find default provider 'notify-osd' of required provider 'notifications'. Not sure if this is related to the issue, but it may be helpful. Removing and reinstalling the notify-osd package doesn't help, though.

I suspect that a particular package causes the problem, but I am not sure which one it is. Any suggestions or tips are very welcome, thanks folks in advance!

Christian

---

### Post by chrarnold on 2012-02-16
Maybe this was posted in the wrong forum, but is there really nobody who came across this issue?

---

### Post by kurt18947 on 2012-02-16
> **chrarnold said:**
> Maybe this was posted in the wrong forum, but is there really nobody who came across this issue?

There's a fair bit of discussion about gnome classic.  Here is one thread with links to others:

[http://ubuntuforums.org/showthread.php?t=1886799&highlight=gnome-fallback](http://ubuntuforums.org/showthread.php?t=1886799&highlight=gnome-fallback)

There was talk at one time that 12.04 would be the last Ubuntu with gnome-session-fallback available.  I don't know if that's still the case or not.  There are other Desktop Environments & Window Managers in various stages of development.  Mate, Mint's cinnamon are a couple frequently discussed.  Installing Xfce-desktop is a viable alternative IMO.

---

### Post by chrarnold on 2012-02-17
Hi,

thanks for the link. However, I think the problem I have may be different. I tried various desktop GUI's (Cinnamon, Gnome classic, Unity, Ubuntu), and in ALL of them, I have the described issue that any changes to the panels are lost after I logout. Thus, there must be something wrong deeper in the system... Do you have any suggestions how to address the problem?

Thanks!

---

### Post by grahammechanical on 2012-02-17
This is the bit that makes it difficult for anyone to offer suggestions:

>  However, after installing some packages (I don't know when exactly the issue occurred),

If you do not know then we do not know. Anything that anyone suggests would be just a guess and may create other problems.

You also say this: 

>  I tried various desktop GUI's (Cinnamon, Gnome classic, Unity, Ubuntu), and in ALL of them, I have the described issue that any changes to the panels are lost after I logout.

Each user interface brings its own libraries and configuration files. There are interdependencies between libraries. You have created an experimental operating system.

Perhaps there are configuration conflicts that would crash another type of OS but not Linux. Sometimes a re-install with a format of the partition is needed to clear up situations like this.

Do you have a separate /home partition that would keep your data and documents safe from format of the / partition.

I dual boot into another install of Ubuntu in another partition and I do all my experiments on that testing install of Ubuntu. I am using it to test 12.04. This is the safest way to experiment.

Some say the the great thing about Linux is the ability to endlessly modify it. It is also the worse thing about Linux because we can turn a working setup into a unworkable one.

Regards.

---

### Post by chrarnold on 2012-02-17
Hi,

I understand that it is difficult to help given that I do not exactly know when the problem occurred the first time. I installed my system 4 days ago, fresh in its own partition, and it seems that it is already broken... Pretty frustrating, as I solely installed common software that I need from the package manager. The additional GUIs like Cinnamon were only installed after the classic GUIs did not work as expected.

It could also be that some of the automatic updates that Ubuntu installed caused the problem. All in all, I think I will disable all updates again, as I did with Ubuntu 10.04. Once I had a working system with no big issues, I deactivated all updates, as I frequently found that updates cause problems somewhere in the system. This seems to be worse with Ubuntu 11.10...

I agree, I will probably install it all over again...Yikes...

Christian

---

