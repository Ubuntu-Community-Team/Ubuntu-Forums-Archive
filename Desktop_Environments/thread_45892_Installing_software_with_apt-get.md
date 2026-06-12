---
title: "Installing software with apt-get"
date: 2005-07-02
forum: Desktop Environments
---

### Post by Astrakan on 2005-07-02
Hi, I'm new to debian-based distribution, and I have a question about installing software.
For example, I want to install octave. I try sudo apt-get install octave -> no packages. Then I try using kynaptic and there is no octave package listed.
Then I try packages.ubuntulinux.org, I download octave, dpkg -i octave...deb -> dependency error, so I download all the dependencies, and the dependencies of the dependencies and then I have octave working.
Now my question, why doesn't apt get see all the packages listed at the url above? Repeating this procedure is very boring (and I have still a lot of packages to install, such as mplayer or VLC), is there a trick to aviud this?
Thanks

---

### Post by bier444 on 2005-07-02
octave is a package of the hoary universe.

have a look at your /etc/apt/sources.list.

--> nano /etc/apt/sources.list

you need two lines like:
deb [http://at.archive.ubuntu.com/ubuntu](http://at.archive.ubuntu.com/ubuntu) hoary universe multiverse
deb-src [http://at.archive.ubuntu.com/ubuntu](http://at.archive.ubuntu.com/ubuntu) hoary universe multiverse

to get the universe and multiverse packages.

after changing the sources.list file, do a apt-get update.

then you will get octave.

bier444

---

### Post by Astrakan on 2005-07-04
Thanks, now it works.

---

