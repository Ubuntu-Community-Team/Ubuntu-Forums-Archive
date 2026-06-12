---
title: "kubuntu-desktop desktop pkg errors"
date: 2008-05-01
forum: Desktop Environments
---

### Post by allent on 2008-05-01
I am trying to install KDE on an existing 8.04 Ubuntu install using the Synaptic Package manager under Gnome.  After selecting the kubuntu-desktop package, about a third of the marked files were retrieved, but the rest failed - the error messages are something like "Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/blahblah.../blahblah](http://us.archive.ubuntu.com/ubuntu/pool/main/k/blahblah.../blahblah)... 404 Not found [IP: 91.189.88.31.80]".

 I am using the default settings for the Manager.  Any ideas what is wrong?  Do I have to add another depository, or is the depository down?

---

### Post by warp99 on 2008-05-02
> **allent said:**
> I am trying to install KDE on an existing 8.04 Ubuntu install using the Synaptic Package manager under Gnome.  After selecting the kubuntu-desktop package, about a third of the marked files were retrieved, but the rest failed - the error messages are something like "Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/k/blahblah.../blahblah](http://us.archive.ubuntu.com/ubuntu/pool/main/k/blahblah.../blahblah)... 404 Not found [IP: 91.189.88.31.80]".

 I am using the default settings for the Manager.  Any ideas what is wrong?  Do I have to add another depository, or is the depository down?

Just an error retreiving the packages.gz file or the package file itself, no big deal. Anyway don't use Synaptic to install kubuntu-desktop instead use aptitude so if you want to remove the kubuntu-desktop later it's easier to purge the files. So open a terminal and do the following:

```
sudo aptitude clean && sudo aptitude autoclean
```
to remove any downloaded packages from the previous attempt and any packages that are no longer available, then:
```
sudo aptitude update
```
and finally:
```
sudo aptitude install kubuntu-desktop
```
during the install just remember when the dialog asks you to keep gdm or use the kdm login manager choose gdm so you can still retain access to your Gnome desktop. After everything is complete issue a 'sudo reboot' and choose 'KDE' from the sessions manager at login to enjoy your new desktop.

---

