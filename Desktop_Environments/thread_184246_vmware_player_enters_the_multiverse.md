---
title: "vmware player enters the multiverse"
date: 2006-05-29
forum: Desktop Environments
---

### Post by ssam on 2006-05-29
> vmware-player (1.0.1-3)

        * debian/copyright:
              o added a clarification about the redistribution in multiverse (as mailed by vmware)

vmware-player (1.0.1-2)

        * Use debconf to prompt user in preinst for license acceptance.
        * Call gtk-update-icon-cache from postinst and postrm a'la dh_iconcache.

vmware-player (1.0.1-1)

        * Initial Debian package release. .

---

### Post by FredB on 2006-05-29
At least !

But I am searching for the true software, not its player only and I cannot get it installing on my up-to-date dapper :(

---

### Post by roshan.s on 2006-05-29
Just noticed this on the dapper-changes list:
[https://lists.ubuntu.com/archives/dapper-changes/2006-May/011770.html](https://lists.ubuntu.com/archives/dapper-changes/2006-May/011770.html)

It seems the freeware VMWare Player is entering multiverse. Not so good from a Free Software point of view, but I guess it could be useful for people who don't want to use QEMU for some reason. Might also make it easier for some people to migrate to Ubuntu if they can keep using Microsoft Windows for some particular application.

The source package has been successfully [built]("https://launchpad.net/distros/ubuntu/dapper/+source/vmware-player/+builds"), so it should be hitting the repositories soon.

Edit: It appears that only the amd64 version has been built so far. For once us 64-bit users get the jump on everybody else!

Edit 1: The VMWare Player kernel module failed to build from source, probably because bzip2 wasn't in the build-deps. Looks like we'll have to wait a while before it's done.

---

### Post by besada on 2006-05-31
Apparently, new packages of this have arrived to the repositories. They seem to have removed the architecture (386-686-k7) specific modules files and instead a new modules deb appeared. Does this one contain all architectures? May I safely update and remove the specific 686 model I was using without problem?

---

### Post by Shay Stephens on 2006-05-31
[QUOTE=roshan.s]...but I guess it could be useful for people who don't want to use QEMU for some reason.[/QUOTE]

The reason I am using vmware instead of qemu, is that qemu is not working 100% for me.  I can't get .net framework loaded right, windows update won't work, and my main reason for using qemu is to get a cd/dvd printer working, but the install won't work in qemu.

It all works perfect under vmware though.

The install for player failed, and it took out my server.  Going to have to start over it looks like :-(

---

### Post by ubuntu_demon on 2006-06-02
warning about vmware-player and possible fix
[http://www.ubuntuforums.org/showthread.php?t=186313](http://www.ubuntuforums.org/showthread.php?t=186313)

---

### Post by ametade on 2006-06-02
Well, I can't start it:

[https://launchpad.net/distros/ubuntu/+source/vmware-player/+bug/47792/](https://launchpad.net/distros/ubuntu/+source/vmware-player/+bug/47792/)

:(

---

