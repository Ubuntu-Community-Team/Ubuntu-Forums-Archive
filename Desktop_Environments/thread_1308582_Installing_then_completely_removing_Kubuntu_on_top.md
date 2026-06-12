---
title: "Installing then completely removing Kubuntu on top of Ubuntu"
date: 2009-10-31
forum: Desktop Environments
---

### Post by wersdaluv on 2009-10-31
I'm planning to test Kubuntu on top of my Ubuntu install. However, I'm being stopped by the inability to easily remove all Kubuntu components that are not part of the Ubuntu desktop.

I have the Ubuntu karmic 64 desktop now. After installing and testing the kubuntu desktop package, I want to completely remove it again (with all its components that aren't also parts of the ubuntu desktop). Any idea how to do this? I remember uninstalling the Kubuntu desktop package and still seeing some residue from the kubuntu desktop.

---

### Post by ShaneR on 2009-10-31
I just tried this and it seemed to the trick for me:

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by wersdaluv on 2009-10-31
Ah cool. Yes, I forgot about aysiu's guide. It's just that, I remember trying this before. I'm not sure if it did the trick for me. Oh well. I'll just do it :)

---

### Post by ShaneR on 2009-11-16
Sorry to bump this, but I can't find an answer.

As I said above, using the code from psychocats appeared to work for me.  However, I decided to install Kubuntu-desktop again to test and it appears that the above left quite a bit laying around.

When installing Kubuntu-desktop clean, in downloads a couple of hundred of packages or so. This time, it only downloaded a small amount and, when I booted into KDE, all my previous settings and changes were still there.

So, how do I completely purge the changes running this meta package makes?

Thanks.

---

### Post by Philippe1 on 2009-11-16
It might be too late but here is my suggestion:

When I want to try something special and am not certain of the consequences, I always do an Image Backup with Clonezilla.
This way, I know I can revert back to when everything was working fine...

Philippe

---

### Post by mrboojive on 2009-11-16
> **ShaneR said:**
> Sorry to bump this, but I can't find an answer.

As I said above, using the code from psychocats appeared to work for me.  However, I decided to install Kubuntu-desktop again to test and it appears that the above left quite a bit laying around.

When installing Kubuntu-desktop clean, in downloads a couple of hundred of packages or so. This time, it only downloaded a small amount and, when I booted into KDE, all my previous settings and changes were still there.

So, how do I completely purge the changes running this meta package makes?

Thanks.

First off, the command did work. You did delete everything that was "installed" by kubuntu-desktop. The reason it only downloaded a few packages the second time was that the installation files from the first time were still cached on your machine. You can delete all cached installation packages using the command: ```
sudo apt-get clean
```Alternatively, you can delete just the cached installation files for packages that you do not currently have installed using the command:```
sudo apt-get autoclean
```

The reason that your settings were still around is that uninstalling a package does not uninstall all settings. To absolutely remove all traces of Kubuntu, change the first part of the that command you used to uninstall from "sudo apt-get remove" to "sudo apt-get purge" and also go into your home directory and delete all config files for Kubuntu, such as the .kde directory and any other .*something* directories that look like they are from KDE programs.

---

### Post by ShaneR on 2009-11-17
Awesome :)

Thanks for that explanation.  Makes sense now.  I'll give it a try soon.

---

