---
title: "gnome libaries for Kubuntu?"
date: 2005-08-13
forum: Desktop Environments
---

### Post by linuxa on 2005-08-13
Hi all

A couple of applications that I'm thinking of installing for Kbuntu seem to have gnome libraries as prerequisites...

Those are:
* Mozilla-firefox
* netapplet (anyone know of another substitute for this that will keep tabs on a wireless network??)

My question is would those gnome libraries affect my KDE in anyway (read: as in break anything)?

I'd appreciate any help on this matter, being a Linux newbie and all :razz: 

Thanks in advance.

---

### Post by Lord Illidan on 2005-08-13
No, they will not break anything... I guess 99% of those who use Kubuntu use Firefox too, even I do.. relax..

They might run slower than they would in a Gnome system, but nothing will be broken..

---

### Post by linuxa on 2005-08-15
Thanks for the reply **Lord Illidan**.

I installed netapplet, unfortunately, I can't seem to find the executable to run it. Typing netapplet in "run command" comes back with "unkown host netapplet". And there doesn't seem to be an entry in usr/bin/.

Could someone please suggest a way to solve this or an alterative app?

Thanks

---

### Post by Gezzer on 2005-08-15
[QUOTE=linuxa]Thanks for the reply **Lord Illidan**.

I installed netapplet, unfortunately, I can't seem to find the executable to run it. Typing netapplet in "run command" comes back with "unkown host netapplet". And there doesn't seem to be an entry in usr/bin/.

Could someone please suggest a way to solve this or an alterative app?

Thanks[/QUOTE]
 in a terminal/konsole try

sudo netapplet
press enter
your password
press enter

see if that works ...

---

### Post by linuxa on 2005-08-17
Thanks for the efforts **Gezzer**. Unfortunately, it doesn't work.

sudo: netapplet: command not found

There doesn't appear to be a file in the bin area. Here's result from the "locate" command:

root@ubuntuLaptop:~# locate -u
root@ubuntuLaptop:~# locate netapplet
/etc/init.d/netapplet
/etc/rc0.d/K20netapplet
/etc/rc1.d/K20netapplet
/etc/rc2.d/S20netapplet
/etc/rc3.d/S20netapplet
/etc/rc4.d/S20netapplet
/etc/rc5.d/S20netapplet
/etc/rc6.d/K20netapplet
/var/lib/dpkg/info/netapplet.postinst
/var/lib/dpkg/info/netapplet.list
/var/lib/dpkg/info/netapplet.prerm
/var/lib/dpkg/info/netapplet.postrm
/var/lib/dpkg/info/netapplet.conffiles
/var/lib/dpkg/info/netapplet.md5sums
/var/cache/apt/archives/netapplet_0.99.4-2ubuntu1_i386.deb
/var/run/netapplet.socket
/usr/share/doc/netapplet
/usr/share/doc/netapplet/README.Debian
/usr/share/doc/netapplet/README
/usr/share/doc/netapplet/changelog.Debian.gz
/usr/share/doc/netapplet/copyright
/usr/share/man/man1/netapplet.1.gz
/usr/share/pixmaps/netapplet.png
/usr/share/applications/netapplet.desktop
/usr/share/netapplet
/usr/share/netapplet/netapplet.glade
/usr/lib/netapplet
/usr/lib/netapplet/netapplet
root@ubuntuLaptop:~#

---

### Post by Nubsauce on 2005-08-18
You could try something like

```
/etc/init.d/netapplet start
``` 

Or it may just need

```
/etc/init.d/netapplet
``` 

See if those help you out.  :)

Regards

EDIT: Run those commands from the command line..  if you weren't sure.  heh.

---

