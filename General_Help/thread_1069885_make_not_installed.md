---
title: "make not installed"
date: 2009-02-14
forum: General Help
---

### Post by versai on 2009-02-14
newbie. check.
frustration. check.

now that that's stated, here's my issue.

i'm trying to install ndiswrapper from source and the error i receive is that "make" is not installed. try "sudo apt-get install make".

i have copies of the .deb packages as well as the tarball in a directory called wireless under home directory. i have unzipped the tarball. cd to the created directory and run make. the above error occurs.

now i would love to use apt-get but in essence i'm trying to install my wifi driver. hence no connection. i'm not sure if the install cd for server contains make but,

running dual-boot ubuntu desktop 8.10 & ubuntu server 8.10
i have no problem installing and getting network connection to work on desktop but the "make not installed" occurs when booted to server.

I appreciate any help.

versai

---

### Post by geirha on 2009-02-14
If the desktop already has make installed, it is likely that the .deb for it is located under *mount-point*/var/cache/apt/archives/

Both the desktop and the server downloads the packages from the same repositories, so it should be equivalent to installing it with apt-get. Except of course, if one of your installs is 32 bit and the other 64-bit.
```
cd *mount-point*/var/cache/apt/archives/
sudo dpkg -i make*.deb
```

---

### Post by cariboo on 2009-02-14
If you install the build-essential package, make will automatically be installed. Why compile ndiswrapper from source when it is included on the both the alterante install and live cd's.

Jim

---

### Post by versai on 2009-02-14
i don't know why i wanted to compile. couldn't figure out how to install the .deb packages, but then figured it out. i assume "apt-get install build-essential" will give me all the tools for the future? i was able to install "make" without any of the dependencies by:

sudo apt-cdrom add <- with each of the respective cd installs
                   <- now i can't figure out how to remove from my sources.list without manually doing it.

right so i figured out how to install the package from a local directory. "dpkg -i" and was able to wrap my xp driver acquire a local ip, and ping inside the network. but i can't ping outside the network. so i have a little more research to do. any help greatly appreciated. 

versai

---

### Post by hyper_ch on 2009-02-14
build-essential contains the essential tools for compiling. However often you will need additional librariers.

you can install .deb files by runing:

```

sudo dpgk -i package.deb

```

---

### Post by versai on 2009-02-14
aha!

everything is working. do get out of the local network i had to take down eth0

sudo ifconfig eth0 down

thanks for the help!

versai

---

