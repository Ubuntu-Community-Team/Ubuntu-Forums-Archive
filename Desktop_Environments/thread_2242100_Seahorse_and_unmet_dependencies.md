---
title: "Seahorse and unmet dependencies"
date: 2014-08-30
forum: Desktop Environments
---

### Post by gordon99 on 2014-08-30
I am running on Xubuntu XFce 14.04 and am trying to get 'keyring' working. I understand I have to use 'Seahorse' but when  tried to install @Password and keys' in the Software Centre it said I had 'unmet dependencies'. 
I then went onto terminal and typed "sudo apt-get install seahorse". The result was as follows:- 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies.
 seahorse : Depends: gcr (>= 3.9.1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages

Can anyone please explain what I can do to fix this problem?

---

### Post by vasa1 on 2014-08-30
It's odd that you don't have **gcr**. From this I get the impression it's present in most flavors of Ubuntu:
```
[11:32 PM] ~ **$ apt-cache show gcr**
Package: gcr
Priority: optional
Section: gnome
Installed-Size: 484
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Josselin Mouette <joss@debian.org>
Architecture: amd64
Version: 3.10.1-1
Replaces: gnome-keyring (<< 3.3)
Depends: dconf-gsettings-backend | gsettings-backend, libc6 (>= 2.4), libgcr-base-3-1 (>= 3.8.0), libgcr-ui-3-1 (>= 3.8.0), libglib2.0-0 (>= 2.32.0), libgtk-3-0 (>= 3.0.0), dbus-x11
Breaks: gnome-keyring (<< 3.3)
Filename: pool/main/g/gcr/gcr_3.10.1-1_amd64.deb
Size: 48294
MD5sum: edb92c7f04fb845de2b4e42753f3e61e
SHA1: 02c557d361a5eb8e4bdc437f7a1989eea47b7f87
SHA256: 7cf626f8e0feb35651534999509afb9301d99db2d9ac887842619f7eb1ac5b60
Description-en: GNOME crypto services (daemon and tools)
 GCR is a library for crypto UI and related tasks.
 .
 This package contains the certificate viewer and prompter service.
Description-md5: ee6145fe2ef6efa76055bc896f49f5f4
Homepage: https://wiki.gnome.org/GnomeKeyring
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 5y
Task: ubuntu-desktop, ubuntu-usb, kubuntu-desktop, kubuntu-full, kubuntu-active-desktop, kubuntu-active-full, edubuntu-desktop, edubuntu-usb, **xubuntu-desktop**, mythbuntu-frontend, mythbuntu-frontend, mythbuntu-desktop, mythbuntu-backend-slave, mythbuntu-backend-slave, mythbuntu-backend-master, mythbuntu-backend-master, lubuntu-desktop, ubuntustudio-desktop, ubuntu-gnome-desktop

```

Is your "Xubuntu XFCE 14.04" a normal clean installation or have you installed/uninstalled a lot of stuff?

---

### Post by gordon99 on 2014-08-30
Hello vasa 1. I had originally installed Ubuntu 14.04 with unity desktop. Although it was only a few weeks ago, I struggle to remember what actions I took to change to Xubuntu xfce. I am as positive as I can be, however, that I have not installed or removed anything I should not have. I did not install Evolution in Ubuntu so I do not know how it might have performed if I had. If there is any doubt could I/should I remove and re-install the complete OS?

---

### Post by vasa1 on 2014-08-30
I don't know what to say: Ubuntu (the Unity one) has gcr and so does Xubuntu. So just installing xubuntu-desktop should not have caused gcr to vanish.

And seahorse should have been installed with Ubuntu (Unity) in the first place. Installing the xubuntu-desktop shouldn't have caused seahorse to vanish.

There's no need to remove anything if you go for a re-install. You can choose to write over your existing installation.

Anyway, I have no first-hand knowledge of seahorse or gnome-keyring.

---

