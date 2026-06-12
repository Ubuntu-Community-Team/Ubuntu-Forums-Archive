---
title: "Several Ubuntu editions on one DVD"
date: 2007-10-31
forum: Development CD/DVD Image Testing
---

### Post by override16 on 2007-10-31
Hi! 
I was wondering if someone know how I can get several of the Ubuntu editions on a bootable DVD. 
I am tired of all the different CD's I need for the different editions. I want Ubuntu (server and desktop edition), Kubuntu and maybe Xubuntu on one bootable DVD. Maybe a menu to choose wich one to boot from.

---

### Post by smartboyathome on 2007-10-31
> **override16 said:**
> Hi! 
I was wondering if someone know how I can get several of the Ubuntu editions on a bootable DVD. 
I am tired of all the different CD's I need for the different editions. I want Ubuntu (server and desktop edition), Kubuntu and maybe Xubuntu on one bootable DVD. Maybe a menu to choose wich one to boot from.

Already done. You can get it at:
[http://cdimage.ubuntu.com/dvd/current/](http://cdimage.ubuntu.com/dvd/current/)

---

### Post by Siph0n on 2007-11-01
That website posted only has the Gutsy lol.... it probably only the Gnome Ubuntu..... I think the thread opener wanted a dvd with the different versions on a single DVD

---

### Post by smartboyathome on 2007-11-01
> **Siph0n said:**
> That website posted only has the Gutsy lol.... it probably only the Gnome Ubuntu..... I think the thread opener wanted a dvd with the different versions on a single DVD

I think that has all 3 DEs on one DVD. I could be wrong though (as I don't have a DVD burner, and haven't tried it).

---

### Post by Jose Catre-Vandis on 2008-04-27
I have been having a look at this proposal over the last few days, since Hardy came out. I too, have a need for desktop, server, alt install, xubuntu alt and kubuntu alt. After much research on the web I have got so far but not a complete solution.

My first attempt was to copy one set of distro files after another into on directory, rename all the respective initrd.gz and vmlinuz files and edit isolinux.cfg. This kinda worke. was able to install from live cd selections, a server and xubuntu (didn't include kubuntu) in my build. But the alt desktop wouldn't work. And everything alternate had a xubuntu "flavour" to it, as this was the last distro I copied over. So plan B.

Build an iso with a simple isolinux directory and modified isolinux.cfg, and then a directory for each distro, copied over from the isos. Each distro needed a hacked initrd.gz as there are files inside it that have paths. There were also some hacks for the live cd initrd.gz to help casper.

So far I have only tried with live cd and server.

On boot I get a selection screen, and each distro will start to run. Live CD borks early on - seems to be looking for the floppy - I think this is a bug with the live cd of hardy. (doesn't happen though when I boot the live iso on its own) The server choice makes a good start of running an installation, but gives up the ghost with an error about release names and bootstrap-base.

So if anyone can point me on from there, I would be grateful. Similarly, if there is interest (support!), I will post up my work so far in terms of the set-up and hacks.

---

### Post by maybeway36 on 2008-04-28
I think the Ubuntu project should do what Debian does: use tasksel on the text-mode installer. The mini.iso already does this, but that doesn't contain ANY packages, which is sort of the opposite of what you want.

---

