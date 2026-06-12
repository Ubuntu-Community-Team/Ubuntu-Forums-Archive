---
title: "Install Ubuntu Desktop to Raspberry Pi Server"
date: 2020-08-20
forum: Desktop Environments
---

### Post by usersystem10 on 2020-08-20
Hi,

I have been trying to install the Ubuntu Desktop to the 64bit version of the Ubuntu Server on a Raspberry Pi 4 without an internet connection.

The Steps I went through where:

1) After Server install, set the date and time
2) Followed the details from this article [https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)
3) Run sudo apt-get update
4) Fix missing file errors from step 3 which meant getting cnf/Commands-arm64/Commands-arm64.xz and i18n/tranlation-en/Translation-en.xz from [http://ports.ubuntu.com/dists/focal/](http://ports.ubuntu.com/dists/focal/) main restricted universe and multiverse.
5) Tried dpkg-query --list to search for ubuntu-desktop and ubuntu-gnome-desktop(although i think that is something else) however it did not list either of these.

Looking around I came across Meta packages that only list files needed or recomended for packages which seem to be vast amounts as seen from this link: [https://packages.ubuntu.com/focal/ubuntu-desktop](https://packages.ubuntu.com/focal/ubuntu-desktop).

Is there a .deb file or compressed file that can be downloaded from the Ubuntu site that would allow the installation of the Ubuntu desktop and others offline?

---

### Post by grahammechanical on 2020-08-20
I think you need to use dpkg-query --list on your off-line repository and look for Gnome 3 and Gnome 3 Shell.  The first one is the desktop enviroment. The second one is the user interface.

Regards

---

### Post by ActionParsnip on 2020-08-21
I suggest you use XFCE of LXDE. They are lighter desktops which will strain the Pi less.

---

### Post by usersystem10 on 2020-08-21
I tried the dpkg-query --list although there was no listing of Gnome 3 or Gnome 3 Shell.

Through the link: [https://packages.ubuntu.com/focal/gnome/](https://packages.ubuntu.com/focal/gnome/) there where a lot of packages listed for Gnome including [gnome (1:3.30+2) [universe]]("https://packages.ubuntu.com/focal/gnome/gnome"), [gnome-core (1:3.30+2) [universe]]("https://packages.ubuntu.com/focal/gnome/gnome-core") and [gnome-shell (3.36.4-1ubuntu1~20.04.2 and others) [security]]("https://packages.ubuntu.com/focal/gnome/gnome-shell").

On the Debian site I found [gnome-shell (3.30.2-11~deb10u1]("https://packages.debian.org/stable/gnome/gnome-shell"), were these the sort of files you where talking about grahammechanical? 

I did come across similar ones for the XFCE system mentioned by ActionParsnip for example [xfdesktop4 (4.12.4-2)]("https://packages.debian.org/stable/xfce/xfdesktop4").

If these are the files implied, is there a location on the Ubuntu or Debian site to download the files and their dependences combined as one file or does it mean that each listed dependency would need to be downloaded along with their own sub-dependences?

I also came across [this link]("http://ports.ubuntu.com/ubuntu-ports/ubuntu-ports/pool/main/g/gnome-desktop3/") with gnome-desktop3 and [this link]("http://ports.ubuntu.com/ubuntu-ports/ubuntu-ports/pool/main/g/gnome-shell/") with gnome-shell which are probably more like it, however they seem very small files.

Would adding the arm64 appropriate files from these previous two links be sufficient to install the Gnome desktop environment and shell or are others required, for example [gnome-session]("http://ports.ubuntu.com/ubuntu-ports/ubuntu-ports/pool/main/g/gnome-session/") [gnome-menus]("http://ports.ubuntu.com/ubuntu-ports/ubuntu-ports/pool/main/g/gnome-menus/") etc?

 If they would be sufficient are the ones to start with [gnome-desktop3_3.37.90.1.orig.tar.xz]("http://ports.ubuntu.com/ubuntu-ports/ubuntu-ports/pool/main/g/gnome-desktop3/gnome-desktop3_3.37.90.1.orig.tar.xz") and [gnome-shell_3.36.4-1ubuntu1~20.04.2_arm64.deb]("http://ports.ubuntu.com/ubuntu-ports/ubuntu-ports/pool/main/g/gnome-shell/gnome-shell_3.36.4-1ubuntu1~20.04.2_arm64.deb")?

---

### Post by grahammechanical on 2020-08-21
I am not sure but I think the the desktop environment and the user interface are made up of a combination of many packages and not 1 or 2 large compressed files. All the available packages are in the Ubuntu repositories and if you have a complete offline repository then all the necessary packages should be in that offline repository.

So, the question in my mind is: What is the command to install Gnome 3? I have found this, which might help you

[https://linuxconfig.org/how-to-install-gnome-on-ubuntu-18-04-bionic-beaver-linux](https://linuxconfig.org/how-to-install-gnome-on-ubuntu-18-04-bionic-beaver-linux)

[https://linuxconfig.org/how-to-install-gnome-on-ubuntu-20-04-lts-focal-fossa](https://linuxconfig.org/how-to-install-gnome-on-ubuntu-20-04-lts-focal-fossa)

Regards

---

### Post by mikewhatever on 2020-08-21
What is "Raspberry Pi Server "? Did they make a special server board?

---

