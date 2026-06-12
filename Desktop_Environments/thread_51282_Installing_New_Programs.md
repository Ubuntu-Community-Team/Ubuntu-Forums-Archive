---
title: "Installing New Programs"
date: 2005-07-23
forum: Desktop Environments
---

### Post by Russ Irwin on 2005-07-23
\\:D/ I am new to kubuntu - How do I install prgrams like Firefox and thunderbird?  Also how would I nstall any Debian packages - my kids love some of the games.

Thanks

Russ the newbie

---

### Post by Xian on 2005-07-23
Programs are installed using [Synaptic](https://wiki.ubuntu.com//SynapticHowto). Deb files are installed by placing them in your /home/username folder and issuing this command:

```
$ sudo dpkg -i nameofpackage.deb
```

---

### Post by Natja on 2005-07-23
Hi,

You can install new programs with synaptic (system > Admin > synaptic). Don't forget to enable extra repos. if you don't find the program you want.

If you want to manually install a .deb package:
sudo dpkg -i your_package.deb

---

### Post by SGC on 2005-07-23
Kubuntu uses kynaptic instead of synaptic , you can find it in:
kmenu -> System -> package Manager (Kynaptic)

How to use kynaptic:
[http://kudos.berlios.de/kf/kf1.html#kynaptic](http://kudos.berlios.de/kf/kf1.html#kynaptic)

Using kynaptic you can search, download, and install thousands of software, but first you need to enable the extra repositories from here:
[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)

Note that the above page is written for ubuntu, so you need to change **gedit** in all commands to **kwrite** or **kate** to make it works with kubuntu

If you want to install .deb file by just clicking on them without typing commands, then search  for program called **kpackage** in kynaptic .

---

