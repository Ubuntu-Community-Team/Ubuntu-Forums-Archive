---
title: "Grub"
date: 2006-06-13
forum: Desktop Environments
---

### Post by dareofficer on 2006-06-13
I have Ubuntu, and Suse 10.1 on my Hard drive.  I had to many part's and re-formated an area.  When I did this I lost my grub screen.  How can I restore this?  I'm lost, and I just got it going right.

Thanks:-({|=

---

### Post by mlind on 2006-06-13
You must boot using Ubuntu's install cd, there's option for recovery mode.
You should be able to get your root partition mounted, and execute upgrade-grub
script.

I've done this few times myself. I've used "alternative" install cd, in which recovery
recovery mode is on text console view. Main thing is that you must get chrooted
to your Ubuntu's root (/) partition and run

```

sudo update-grub

```

if this produces any errors, you must reinstall grub to the device which is first on the
boot order. Usually /dev/hda. You should find this out though before executing
the command.

```

sudo grub-install /dev/hda

```

---

### Post by dareofficer on 2006-06-13
Thanks for the response.  I can't find anywere on the cd that says system restore?  Where is that at?  Do I need a different cd?  I have the new one, that loads from the cd, and I see an install icon.

Thanks.

---

### Post by Fatjoint on 2006-06-13
[QUOTE=dareofficer]Thanks for the response.  I can't find anywere on the cd that says system restore?  Where is that at?  Do I need a different cd?  I have the new one, that loads from the cd, and I see an install icon.

Thanks.[/QUOTE]


It should be in the text menu before actually booting into Linux-Live

---

### Post by mlind on 2006-06-13
[QUOTE=dareofficer]Thanks for the response.  I can't find anywere on the cd that says system restore?  Where is that at?  Do I need a different cd?  I have the new one, that loads from the cd, and I see an install icon.

Thanks.[/QUOTE]

I've only used the "alternate" cd, which is the old ncurses (text-mode) based installer
which can be found from each Ubuntu's [mirrors]("http://ftp.estpak.ee/pub/ubuntu-releases/6.06/")

full url is [http://ftp.estpak.ee/pub/ubuntu-releases/6.06/ubuntu-6.06-alternate-i386.iso](http://ftp.estpak.ee/pub/ubuntu-releases/6.06/ubuntu-6.06-alternate-i386.iso)

I don't know if new expresso install cd contains recovery mode, I think it should..
If you proceed to install phase, does it allow you to boot already installed system?

---

### Post by dareofficer on 2006-06-13
I can't find it anywhere.  Just a new install.

---

### Post by mlind on 2006-06-13
[QUOTE=dareofficer]I can't find it anywhere.  Just a new install.[/QUOTE]

Ok, download that alternative cd then and burn it. It works atleast.

---

