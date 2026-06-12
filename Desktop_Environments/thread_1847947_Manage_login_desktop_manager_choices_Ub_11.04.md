---
title: "Manage login desktop manager choices? Ub 11.04"
date: 2011-09-21
forum: Desktop Environments
---

### Post by BanderSnoot on 2011-09-21
Hi folks,

A little background: I installed 11.04, and gave Unity a try.  After a short while I decided I hated the way screens were managed, and that stupid menu on the left is far less convenient than cascading menus.  I tried to manage it with Compiz, but it seemed that everything I tried made things worse.

So I installed GNOME3.  But I kept trying to make Unity do what I want with Compiz.  After doing "unity --reset" five times I decided I'd had enough and de-installed Compiz.

Now I am stuck in an in-between state where I have both features of Unity and GNOME.  When I'm at the login screen, selecting "ubuntu classic" no longer works correctly.  The only thing that works as I'd expect is "ubuntu classic (no effects)."

Can I de-install and re-install GNOME?  How can I get GNOME and the login choices reset to their original state?  I am afraid of making things worse.

Thanks.

---

### Post by Krytarik on 2011-09-21
Generally following the instructions from this [guide]("http://ubuntuforums.org/showthread.php?t=1742343"), run:
```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:gnome3-team/gnome3
sudo apt-get update
sudo apt-get dist-upgrade
```Then also make sure the "ubuntu-desktop" meta-package is installed, as with the removal of Compiz, you must have broken it. Compiz is also the window manager of "Ubuntu Classic", and that's why you have issues with those.
```
sudo apt-get install --reinstall ubuntu-desktop
```Good luck!

---

### Post by BanderSnoot on 2011-09-22
Just to clarify, I believe I only removed the Advanced Settings ccsm app.  I'll check though.

I saw that [HOW TO] topic you referenced.  I am concerned about all the disclaimers and qualifications.  I'll give it more study.

When I get home tonight I'll try the steps you listed, and share the results.

Thanks.

---

### Post by BanderSnoot on 2011-09-22
I tried what was suggested, didn't make any difference.

One part which seemed to go awry:
~~~~~~~~~~~~~~~~~~~~
dad@DadUbuntu11:~$ sudo ppa-purge ppa:gnome3-team/gnome3
Updating packages lists
PPA to be removed: gnome3-team gnome3
Warning:  Could not find package list for PPA: gnome3-team gnome3
~~~~~~~~~~~~~~~~~~~~

I thought this might mean I hadn't installed GNOME correctly (I just used the Software Center) so I tried:
~~~~~~~~~~~~~~~~~~~~
dad@DadUbuntu11:~$ sudo add-apt-repository ppa:gnome3-team/gnome3
[sudo] password for dad: 
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv 9D542E3D52C801D9F8E31682F1773AF13B1510FD
gpg: requesting key 3B1510FD from hkp server keyserver.ubuntu.com
gpg: key 3B1510FD: public key "Launchpad PPA for GNOME3 Team" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
dad@DadUbuntu11:~$
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The long and the short of it is none of this seems to work.

(And I didn't de-install compiz earlier, only the ccsm.)

But I tried the 'sudu apt-get install --reinstall ubuntu-desktop' and it did something quickly, but didn't make any difference.

So when I choose "ubuntu classic" from the login I mostly get Unity.

I'm not complaining too loudly because I like the "classic (No effects)"

But I don't like that I screwed the desktop system up and can't make it right.

Does anyone else have any ideas?

---

