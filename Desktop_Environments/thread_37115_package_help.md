---
title: "package help"
date: 2005-05-25
forum: Desktop Environments
---

### Post by saintpa on 2005-05-25
I installed an unstable version of libc6 (2.3.2.ds1-22) via dpkg. Now whenever I do dist-upgrade, the apt-get reports a dependency conflict:

The following packages have unmet dependencies:
  libc6-dev: Depends: libc6 (= 2.3.2.ds1-20ubuntu13) but 2.3.2.ds1-22 is installed
  libc6-i686: PreDepends: libc6 (= 2.3.2.ds1-20ubuntu13) but 2.3.2.ds1-22 is installed
  locales: Depends: glibc-2.3.2.ds1-20ubuntu13
E: Unmet dependencies. Try using -f.

How can I revert libc6 to ubuntu version to resolve this conflict? Any help would be appreciated.

---

### Post by Xian on 2005-05-25
What happens when you issue the command below:
```
$ sudo apt-get -f install
```

---

### Post by saintpa on 2005-05-25
This is what happens if I do sudo apt-get -f install:

Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  build-essential g++ g++-3.3 language-pack-en language-pack-en-base libc6-dev
  libc6-i686 libstdc++5-3.3-dev libtool locales lsb ubuntu-base ubuntu-desktop
  zlib1g-dev
The following held packages will be changed:
  libc6-dev libc6-i686
0 upgraded, 0 newly installed, 14 to remove and 2 not upgraded.
Need to get 0B of archives.
After unpacking 44.2MB disk space will be freed.
Do you want to continue [Y/n]? 

I promptly entered n to stop further destruction of my system :-(.

---

### Post by Xian on 2005-05-25
[QUOTE=saintpa]I promptly entered n to stop further destruction of my system :-(.[/QUOTE]
It's giving you the necessary changes to resolve the dep errors.
Not saying that it is the best solution.....
[QUOTE=saintpa]How can I revert libc6 to ubuntu version to resolve this conflict? Any help would be appreciated.[/QUOTE]
You'll have to fill in the blanks of course but this command should work:

```
$ sudo aptitude install <pkgname>=<version>
```

---

### Post by saintpa on 2005-05-25
It gives me very similar answers to apt-get -f install:

$ sudo aptitude install libc6=2.3.2.ds1-20ubuntu13
Password:
Reading package lists... Done
Building dependency tree
Reading extended state information
Initializing package states... Done
The following packages will be automatically REMOVED:
  gnome-volume-manager gthumb hal hal-device-manager hwdb-client
  libgphoto2-2 libgphoto2-port0 libsane libusb-0.1-4 python-imaging-sane
  python2.4-imaging-sane sane-utils ubuntu-base ubuntu-desktop usbutils
  xsane
The following packages will be DOWNGRADED:
  libc6
The following packages have been kept back:
  libxvidcore4 mplayer-386
The following packages will be REMOVED:
  gnome-volume-manager gthumb hal hal-device-manager hwdb-client
  libgphoto2-2 libgphoto2-port0 libsane libusb-0.1-4 python-imaging-sane
  python2.4-imaging-sane sane-utils ubuntu-base ubuntu-desktop usbutils
  xsane
0 packages upgraded, 0 newly installed, 1 downgraded, 16 to remove and 2 not upgraded.
Need to get 4822kB of archives. After unpacking 26.9MB will be freed.
Do you want to continue? [Y/n/?] n
Abort.

---

### Post by Xian on 2005-05-25
[QUOTE=saintpa]It gives me very similar answers to apt-get -f install:[/QUOTE]
Yeah, the command works fine as I see the package listed to be downgraded.
I honestly can't imagine what else could be causing all those conflicts.

Open Synaptic and click on the 'Status' box.
Look under the heading "Installed (Local or Obsolete)".

Are there some other packages there which are foreign to the Hoary APT repos?
If so, I'd suggest trying to narrow down which one(s) are possibly the culprit.

---

### Post by saintpa on 2005-05-26
Listed there are two packages:

libc6 (2.3.2.ds1-22)
libusb-0.1-4 (2:0.1.10a-10)

---

### Post by Xian on 2005-05-26
Can you use the libusb-0.1-4 (1:0.1.8-17) instead in the Hoary repos?

---

### Post by saintpa on 2005-05-26
Sure, I can revert to the stable libusb. How do I do that?

---

### Post by Xian on 2005-05-26
What is the output of this command (it's a little long):

```
$  sudo aptitude install libc6=2.3.2.ds1-20ubuntu13 libusb-0.1-4=1:0.1.8-17ubuntu2
```

---

### Post by saintpa on 2005-05-26
That does the trick. Thanks a lot of your help!

---

