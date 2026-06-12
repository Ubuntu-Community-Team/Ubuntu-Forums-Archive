---
title: "Missing Indicator App icons"
date: 2011-11-09
forum: Desktop Environments
---

### Post by r_avital on 2011-11-09
Using Lucid 10.04 2.6.32-35-generic 64 Bit.

This morning I had 2.6.32-34-generic.  Some of the icons in Indicator Applet on my top panel went missing (gnome).  Specifically:

Network
Keyboard layouts (flags)
Clamav
Klipper

Found a thread here that discusses a solution (message #6, at [http://ubuntuforums.org/showthread.php?t=1713317](http://ubuntuforums.org/showthread.php?t=1713317))

This is in Natty testing and discussion, and it is closed.

The post refers to downloading package libappindicator1_0.2.99-0ubuntu1 from here:
[https://launchpad.net/ubuntu/+source/libappindicator/0.2.99-0ubuntu1](https://launchpad.net/ubuntu/+source/libappindicator/0.2.99-0ubuntu1)

And then instructs to run the following:

```
sudo dpkg -i libappindicator1-0.2.99-0ubuntu1_amd64.deb
```Problem is, the .deb package in question is not at that location.  

Can anyone help with finding this file?  All my google searches return nothing but the original post.

This was working perfectly until this morning.  installed updated 10.04 2.6.32-35-generic but that had no effect on this problem.

Sorry for my bozosity, I would really, really like to recover these icons, rather than keep the klamav utility minimized all the time and have to re-launch utilities just to find out my network connectivity status or current keyboard layout - not to mention klipper is unusable without that icon.

Please, any thoughts would be appreciated.

Thanks in advance

---

### Post by r_avital on 2011-11-09
Update:  Found the file, ran it in gdebi, which complains about an unsatisfied dependency.

Before I go chasing after dependencies, can someone please suggest a better solution, other than upgrading to Natty?  I mean, my 10.04 is LTS, and this problem was obviously caused by some previous upgrade.  Does it really mean I'm forced to use a previous upgrade like 10.04 2.6.32-32-generic until the next LTS release?

---

