---
title: "install from a archive and WITHOUT INTERNET CONNECTION"
date: 2010-04-18
forum: Desktop Environments
---

### Post by Antoine dpt on 2010-04-18
hello guys,

I bought a DVD from LinuxUSer and I have uppacked the archive to install virtualbox. I DO NOT HAVE INTERNET on the machine I am installing virtualbox. So i can't use apt-get.

after extracting the archive I have 230Mb of data and not a simple "install.exe" file ....

I have some kmk file, some config.vbs file etc....

I suppose this may be the source code and I am suppose to compile something. Can someone help me how to go about this?

how to I launch this install? help before I go back to Windows....

Antoine

---

### Post by Untitled_No4 on 2010-04-18
The archive you unpacked, was it a *.deb file or a .tar.gz file?

If it was a deb file you don't need to unpack it. In the same folder where the .deb file resides run the following (assuming filename is virtualbox.deb):
```
sudo dpkg -i virtualbox.deb
```

If it's the source code you have, look at the installation instruction here: [http://www.virtualbox.org/wiki/Linux%20build%20instructions](http://www.virtualbox.org/wiki/Linux%20build%20instructions)

You need to follow the sections titled Building VirtualBox and Running Your Build.

However if you are new to Linux perhaps compiling isn't the best option. If you have another computer which is connected to the Internet you can download the above VirtualBox deb file from here:
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by Antoine dpt on 2010-04-19
thanks.

yes it is the source code I have.

I tried to do from the deb file but when you install it it starts asking your for depencies that I don't have. So I download them and can't even install those because they again depend on something else.

same with the built. They ask tons of lib and package and pretty garantee that if I tried to install any it will tell me to download some more depencies.

what I need is a tool that scan a package, calculate all the depencies and the depencies of the depencies etc... from that i will get a list of all the deb file I REALLY need to download from the NED. I can then burn a disk and go to the computer where I want to install this.

do you know if such things exist?

---

### Post by __init__ on 2010-04-19
Apt-get can do it without extra aid. It have one handy option: --print-uris. You can just run "apt-get install <package list> --print-uris" and it will print information about all debs you need for full installation of this packages. Or run "apt-get install -f --print-uris" to resovle all current dependency problems with already installed packages.

I sometimes use following script to clean apt-get output leaving only uris in it.
```
#!/bin/bash

apt-get install $1 --print-uris --yes | sed -n "s/^'\([^']*\)'.*$/\1/p"

```
Copypaste code to the file, save it under the name, let's say, "apt-uris", make it executable ("chmod +x apt-uris" in console), and run it like "./apt-uris virtualbox-ose > deb-uris.txt" or "./apt-uris -f > deb-uris.txt" for example.

---

### Post by _0R10N on 2010-04-19
I'm wondering if you couldn't install the required dependencies from your host CD/DVD installer. Remember to edit your sources.list (and perform an apt-get update) so apt-get searches only among the packages on your CD/DVD.

I can't remember, but I think that VirtualBox doesn't required any package that isn't bundled in the DVD.

Kind regards!

_0R10N >>

---

