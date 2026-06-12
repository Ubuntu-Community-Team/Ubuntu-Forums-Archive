---
title: "Quick question about &quot;make&quot;"
date: 2006-08-20
forum: Desktop Environments
---

### Post by faceoftheearth on 2006-08-20
Hi, 

I'm trying to install network manager and the newest drivers for my IPW2915 using [this]("http://www.ubuntuforums.org/showthread.php?t=125150&highlight=IPW2915") guide. I am having a problem when it says "make." I'm fairly new to Linux so I may just be missing something huge, but when I simply type make at the terminal when I'm in the appropriate directory nothing happens. Here is what I am doing. This is from the section entitled "ieee80211 subsystem for any driver". I really hope this is an easy fix because I've been using Linux for a year or so and have never been able to get make to work right. 

Thanks

```
gerryj@VisViva:~/wpa/ieee80211-1.1.14$ sudo rm -rf /usr/src/linux-headers-$(uname -r)/include/net/ieee80211*
gerryj@VisViva:~/wpa/ieee80211-1.1.14$ sudo rm -rf /usr/src/linux-headers-$(uname -r)/include/config/ieee80211*
gerryj@VisViva:~/wpa/ieee80211-1.1.14$ make
bash: make: command not found
gerryj@VisViva:~/wpa/ieee80211-1.1.14$ sudo sh make
sh: make: No such file or directory
gerryj@VisViva:~/wpa/ieee80211-1.1.14$ ls
CHANGES                 ieee80211_crypt_tkip.c  ieee80211_tx.c  Makefile
GIT_SHA1                ieee80211_crypt_wep.c   ieee80211_wx.c  net
idvals                  ieee80211_geo.c         INSTALL         remove-old
ieee80211_crypt.c       ieee80211_module.c      in-tree
ieee80211_crypt_ccmp.c  ieee80211_rx.c          LICENSE
```

---

### Post by aysiu on 2006-08-20
Let me just say that I have no idea about networking or drivers.

That said, in order to install *make*, you'll need a Ubuntu CD (either the Desktop CD or Alternate CD). Paste these commands in the terminal. Then, try again. ```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by faceoftheearth on 2006-08-20
Heh, yeah, I forgot Ubuntu doesn't come with GCC. Now it's saying I need to install gnome-common from the Gnome cvs. How do I do that? 

Thanks for your suggestion :)

---

### Post by aysiu on 2006-08-20
There I can't help you. I don't even know what cvs is...

---

### Post by jackn on 2006-08-20
gnome-common is a Ubuntu package. You can use Synaptic, which should do for most purposes.

As with all packages, however, the Ubuntu repositories may not contain the latest version of any software, as only security updates are integrated into the packages between releases. 

If you wish to or need to go for the latest version, you go to the CVS repository. 

Concurrent Version System allows developers to keep track of the versions of the software as they are deposited into the CVS repository. Don't know the technicalities, but the big deal seems to be that multiple users (developers) can interact with the same working version and modify it. CVS seems to do the same thing that SubVersioN (SVN) does.
So, CVS repositories allow you to checkout the latest version of software.


To checkout the latest version and have the command line tools for CVS, you can use Synaptic for the CVS ubuntu package.

A CVS how-to:
[http://badgertronics.com/writings/cvs/command-line.html](http://badgertronics.com/writings/cvs/command-line.html)

In case it's useful, about installing from a tarball: [http://www.linuxforums.org/forum/suse-linux-help/16344-massive-newb-question.html](http://www.linuxforums.org/forum/suse-linux-help/16344-massive-newb-question.html)

HTH,
Jackn

---

### Post by OffHand on 2006-08-20
> **aysiu said:**
> There I can't help you. I don't even know what cvs is...

[http://www.nongnu.org/cvs/](http://www.nongnu.org/cvs/)

---

### Post by faceoftheearth on 2006-08-21
Thank you so much for the full reply to my post. I'm still getting the hang of the whole CVS way of installing things and the Linux way too using tarbells. The next thing I need to know is where exactly all the stuff that's installed goes. In Windows I can find settings and files for programs in Program Files but I have no idea where to look in Linux since they seem to be stored all over.

---

### Post by peabody on 2006-08-21
> **faceoftheearth said:**
> Thank you so much for the full reply to my post. I'm still getting the hang of the whole CVS way of installing things and the Linux way too using tarbells. The next thing I need to know is where exactly all the stuff that's installed goes. In Windows I can find settings and files for programs in Program Files but I have no idea where to look in Linux since they seem to be stored all over.

Yes, unfortunately, things seem complicated in Linux when it comes to the filesystem.  This is largely for historical reasons.  In a command line environment, it's useful to have all binaries in one folder with the rest of all the binaries on the system, while their resources are stored elsewhere.  Here's all you really need to know:

/usr <-- Almost all package managed software (stuff from synaptic) is installed here

/usr/local <-- Stuff from tarballs almost always installs here by default.

Within those folders are several of the same sub folders:

bin <-- the executables go here
sbin <-- executables that are normally only run as root go here
share <-- documentation and application resources go here

There are more folders, but those are generally the only folders you need to worry about.  Also, all system wide configurtion goes in /etc (packaged software) or /usr/local/etc (tarball software).  User specific configuration is normally stored in hidden folders in your home directory.

---

