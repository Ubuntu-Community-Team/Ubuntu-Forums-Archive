---
title: "New kid on the block here!"
date: 2005-07-03
forum: Desktop Environments
---

### Post by anxietyzone on 2005-07-03
Hi

I am a long time Linux user and have tried various distros over the last 7-8 years including Debian, Gentoo, Mandrake, etc, and finally ended up going with the "industry standard" Red Hat distro and then Fedora (I'm currently using FC4). Ok, so you have a little history from this old grey-haired guy now.

For almost 5 months, I have noticed Ubuntu soaring in the ratings (number 1# spot) over at Distrowatch.org) and so the other day I became curious and DL the Ubuntu LIVE CD. Both my old freind/room mate and myself were impressed but I did some Googling and stumbled onto an old (archived) Ubuntu forum where someone was asking if there was an easier way to install .DEB's than "apt-get" (via the terminal) and the answer was no.

I remember back in the day when all I had to do was click on a program from the main Debian site and the package manager would automatically pop up and install my software. I'm assuming the new(er) version of Ubuntu handles packages in a similar, user-friendly fashion?.

I downloaded the install ISO just an hour ago and it will take some prodding and pushing to get me to replace Fedora 4 (an old, comfortable shoe now) with Ubuntu but I can tell you that I was very impressed with Debian from the early days and even more impressed with Ubuntu (which I assume uses the .DEB format for it's packages(?). Just wondering if you can still "click & install" like the early days. 

Anyway, looks good so far my Linux freinds.

- Regards, an old Linux guy

---

### Post by tread on 2005-07-03
Welcome! For click and install, try synaptic .. it should be under system->administration->synaptic

Alternately, if you like the console, there is a gui program called aptitude which rocks synaptic's socks off :)

---

### Post by mtron on 2005-07-03
ubuntu comes with an very easy to use apt gui called [synaptic](http://www.nongnu.org/synaptic/images/0.53-main.png)  package manager.

just search - click - apply and it installs.

but i still prefer the terminal why? i dunno, for me it's just easier to have my commands then navigating through menus.

some useful apt-get commands: 
(most operations require root privilegs, so run them with "sudo" or switch to the root user with "sudo -s -H")

apt-get install <packagename>
This will install a package.

apt-get upgrade
This will upgrade packages to the most recent versions. However, packages will not be updated with this command if it would require other packages to be either removed or installed.

apt-get dist-upgrade
This is quite simliar to apt-get upgrade, except that it will remove or install any programs needed to ensure that all packages are at the most recent version.

apt-get remove   <packagename>
This will remove a package and leave it's configuration files.

apt-get --purge remove <packagename>
Quite simply, this will do the same as apt-get remove , but it also deletes the configuration files as well.

apt-cache search <value>
This will search the descriptions of packages for the requested pattern.

apt-cache show <packagename>
This will show the description of the supplied package.

dpkg -s <packagename>
This will give information about a package, including configuration files, a description, dependencies, and other facts.

dpkg -S <packagename>
apt-file search
Will attempt to find out which package contains this file.

apt-file list <packagename>
dpkg -c <packagename>
This will return a list of all files in this package.

auto-apt run <packagename>
This will attempt to run a command, most often "./configure", and attempt to download any packages that are needed to fill it's dependencies. It takes the dependency hunting out of building from source.

apt-get update
apt-file update
auto-apt update
This will update the package lists to the most recently available versions (within the selected repositories as seen in /etc/apt/sources.list)

---

### Post by anxietyzone on 2005-07-03
[QUOTE=tread]Welcome! For click and install, try synaptic .. it should be under system->administration->synaptic

Alternately, if you like the console, there is a gui program called aptitude which rocks synaptic's socks off :)[/QUOTE]

Thank you for the fast response!. I will indeed try it. I've used Apt/Synaptic on RH and FC but did not know it could be used on Ubuntu (I've been using YUM (via the terminal since FC4).

---

### Post by varunus on 2005-07-03
I'm not sure where you got that info from, that Ubuntu needed the console, since Synaptic has been in the Ubuntu default install since its first release.

I'm sure you'll like the apt package system just as well as the rpm one (if not better).  Most people I know that have switched from Red Hat to Ubuntu have been amazed at the ease of using Synaptic; it comes set up for you out of the box (no apt configuration like with Fedora).If you have any old packages that you can't find Debian or ubuntu versions of, you can use the "alien" utility to convert .rpms to .debs.  Enjoy.

---

### Post by udha on 2005-07-04
apt-get
synaptic
or to work directly with .deb files i think you can use dpkg

---

