---
title: "Help!!!!"
date: 2006-06-03
forum: Desktop Environments
---

### Post by Rasitiln on 2006-06-03
I tried to install rxvt-unicode_7.7-4 from a deb sarge archive and things went wrong.


```
root@spect0:/home/specter/MyDownloads# apt-get install
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  libc6: Depends: tzdata but it is not installable
  libc6-amd64: Depends: libc6 (= 2.3.6-0ubuntu20) but 2.3.6-11 is installed
  libc6-i686: PreDepends: libc6 (= 2.3.6-0ubuntu20) but 2.3.6-11 is installed
  liburi-perl: Depends: data-dumper
  perl: Depends: perl-base (= 5.8.7-10ubuntu1) but 5.8.8-4 is installed
  rxvt-unicode: Depends: libgcc1 (>= 1:4.1.0) but 1:4.0.3-1ubuntu5 is installed
E: Unmet dependencies. Try using -f.

```

I cant apt-get anything and they wont fix. is there a way I can make it install from the ubuntu mirrors again?? :confused: :confused: :confused:

---

### Post by croak77 on 2006-06-03
If you have Synaptic installed, look in  your System -> Administration -> Synaptic Package Manager, select Edit -> Fix Brocken Packages from the pull down menu.

---

