---
title: "Messed up Xubuntu trying to replace thunar"
date: 2014-08-14
forum: Desktop Environments
---

### Post by geekyhawkes on 2014-08-14
Hello;

I was trying to replace thunar on my xubuntu machine and now have messed up my environment.  Everytime I try to delete or open an application on the desktop I get an error asking for thunar desktop service (the requested operation could not be completed: Failed to execute /usr/bin/Thunar:Success).  I have thunar installed and it opens any folders I select but no idea what the desktop service is or how to install it (i tried sudo apt-get install thunar-desktop* with no luck).

I also have messed up my mime types in the process - everytime I apt-get upgrade I get errors moaning about the mime settings but have no idea what I did (lesson in not rushing and making notes) to mess them up.  The mime error is below:

```
Processing triggers for shared-mime-info (1.2-0ubuntu3) ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
```

Any help well received please - come back thunar all is forgiven!

---

### Post by geekyhawkes on 2014-08-16
can anyone help please? This is driving me crazy!

---

### Post by vasa1 on 2014-08-16
The mime type errors make me think you've installed something from the KDE world. See [https://bugs.launchpad.net/ubuntu/+source/shared-mime-info/+bug/289592](https://bugs.launchpad.net/ubuntu/+source/shared-mime-info/+bug/289592) and [http://ubuntuforums.org/showthread.php?t=1979924](http://ubuntuforums.org/showthread.php?t=1979924)

Why don't you just do a clean reinstall and, in future, remember that changing the file manager can also affect your "desktop" because file managers such as Nautilus, PCManFM, and Thunar also "manage" the desktop.

---

### Post by Rob Sayer on 2014-08-16
It's hard to really say because it's not really clear what you did to 'replace' Thunar.

It's certainly possible that the 'unknown mime type' messages have to do with KDE apps.  I use Dolphin on my Xubuntu 14.04 setup.  Actually I install Dolphin on every linux DE.  I don't like Thunar anyway.  I've gotten the same error messages a number of times and it hasn't caused any problems at all.

Here's an explanation of Mime types:

[http://askubuntu.com/questions/16580/where-are-file-associations-stored](http://askubuntu.com/questions/16580/where-are-file-associations-stored)

But I never tried to 'replace' Thunar.  Uninstalling it would likely also uninstall other XFCE packages that I'd want to keep.  If that's what happened in your case a clean reinstall may be ultimately the easiest way.  I've reinstalled a few times because it was simplest.

---

### Post by vasa1 on 2014-08-16
> **Rob Sayer said:**
> It's hard to really say because it's not really clear what you did to 'replace' Thunar.

It's certainly possible that the 'unknown mime type' messages have to do with KDE apps.  I use Dolphin on my Xubuntu 14.04 setup.  Actually I install Dolphin on every linux DE.  I don't like Thunar anyway.  I've gotten the same error messages a number of times and it hasn't caused any problems at all.

...

But I never tried to 'replace' Thunar.  Uninstalling it would likely also uninstall other XFCE packages that I'd want to keep.  If that's what happened in your case a clean reinstall may be ultimately the easiest way.  I've reinstalled a few times because it was simplest.

I hope you don't mind my saying that I've read about your preference for Dolphin quite often. My concern is that something happens to newish users who may get the impression that replacing a file manager is a trivial matter. They *could* break something in the process. So, my suggestion is that when recommending Dolphin, you point to details on how exactly to install it as you intend.

---

### Post by geekyhawkes on 2014-08-19
I didnt uninstall thunar but tweaked a bunch of files (that I have forgotten...not useful I know) to try and replace thunar as the default.  The mime type tweaking was part of that process.  

I dont want to reinstall my entire machine as thats a huge job and its just about how I like it (apart from this issue).

Is there some way I could force thunar to reinstall and overwrite all the files it needs for a default behaviour?

---

