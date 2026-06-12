---
title: "Steam Install Fails, Missing files."
date: 2015-10-17
forum: Gaming &amp; Leisure
---

### Post by bman on 2015-10-17
When I try to install Steam in the Terminal I get this.

The following packages have unmet dependencies:
 steam:i386 : Depends: libgl1-mesa-dri:i386 but it is not going to be installed
              Depends: libgl1-mesa-glx:i386 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


I am running 15.04 and all topics related to this seem to be 14.04. Any ideas?

---

### Post by R33D3M33R on 2015-10-17
First try to run:

```
sudo apt-get install -f
```

---

### Post by bman on 2015-10-17
I did that and got.

The following packages were automatically installed and are no longer required:
  libqt4-opengl libqtwebkit4 linux-headers-generic linux-image-generic python-appindicator python-gconf python-pexpect python-support thermald
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 10 not upgraded.

---

### Post by Bucky Ball on 2015-10-17
Try

```

sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

Are you [following any guides]("https://wiki.ubuntu.com/Valve") to do this? A 14.04 guide should be fine.

---

### Post by bman on 2015-10-17
No guides. I did all that, still the same errors.

---

### Post by Sorawit_Kongnurat on 2015-10-23
I seem to have this problem too on 14.04. Were you able to solve it and may I ask how cause I'm stuck.

---

### Post by Bucky Ball on 2015-10-23
> **Sorawit_Kongnurat said:**
> I seem to have this problem too on 14.04. Were you able to solve it ...

It appears not.

> **bman said:**
> No guides. I did all that, still the same errors.

Perhaps start a new thread with a descriptive title and outline your issue precisely as you can. They are very rarely identical problems (user is on 15.04 and you are on 14.04, which there are apparently a lot of guides for) unless it is a bug, and they are usually known. Good luck. :)

---

### Post by brian-mccumber on 2015-10-23
I had problems installing Steam using the software manager and the terminal so I used the install link at the Steam website to install it and it worked the first time with no problems.

[http://store.steampowered.com/about/](http://store.steampowered.com/about/)

---

### Post by myromance123 on 2015-11-05
> **bman said:**
> When I try to install Steam in the Terminal I get this.

The following packages have unmet dependencies:
 steam:i386 : Depends: libgl1-mesa-dri:i386 but it is not going to be installed
              Depends: libgl1-mesa-glx:i386 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


I am running 15.04 and all topics related to this seem to be 14.04. Any ideas?

Usually when I receive the error that states I have held broken packages I'll open a terminal and enter the following:
```
sudo dpkg --configure -a
```

This has worked most of the time for me. Additionally, make sure you can still update Ubuntu. If you can't run the updater (GUI), or it gives you warning messages then you might have a PPA installed that is messing things up. You will need to remove that PPA for now.

If you are on the open source Mesa graphics drivers, I would advise you to uninstall Wine at least until you've installed Steam. I've found on several occasions that Wine prevents certain graphics libraries from being installed due to clashes.

If you could provide what graphics card you are using, and what graphics driver you have installed, we would have a better picture of your system and where the issue might be coming from.

One last idea, have you tried downloading Steam directly from the Steam website? It will come in a .deb form, and all you have to do is double click it to run the installer. It will open up in the Ubuntu Software Center, and it may help you overcome your issue as brian-mccumber has mentioned. It's always best to exhaust as many avenues as you can.

---

