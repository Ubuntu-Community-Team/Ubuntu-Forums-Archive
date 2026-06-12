---
title: "Help Grub Problems"
date: 2009-01-22
forum: General Help
---

### Post by SikEnCide on 2009-01-22
Ok, So I decided to remove Ubuntu to gain back extra HDD space on my laptop. Previously I have done this simply by booting with a live Ubuntu CD running Gparted and then using an XP cd to fixmbr.

My problem now is I am running Vista, and the Vista dvd I have is not working. Is there any way I can get rid of grub because its throwing the Error 22.

I want to restore Vistas loader but I have no Vista dvd and no way to burn a new copy.  I am currently posting using a Ubuntu live cd

I did find this...
[http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/)

Does anyone know if it works??

---

### Post by logos34 on 2009-01-22
I don't think ms-sys is in the 8.04 or 8.10 repos, but you can find a .deb pkg [here]("http://ftp.debian.org/debian/pool/main/m/ms-sys/").  Or compile it from tar.gz source (you can do both from the live cd)

Not sure if it works with vista though (you might also have to use the -p option due to some bug in the 2.6 linux kernel--see [this]("http://ms-sys.sourceforge.net/"))

good luck

---

### Post by SikEnCide on 2009-01-22
Yeah I had to find a .deb because it was not in the repos. This however did not work.. Right now I am on a live cd and hopefully before class I can reinstall ubuntu on a smaller partition and this should hopefully reinstall grub.  A temporary fix till I can burn off another vista dvd.  After That I will be removing ubuntu, most likely until I get a bigger hard drive.

I also wanted to try some other linux distros out like mandriva or gentoo.

Thanks for all your guys help.

---

### Post by caljohnsmith on 2009-01-22
When you say it didn't work, can you be more specific? Another way to install a Windows equivalent MBR to a drive is with:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
And change "sda" if your Vista drive is different. If you decide to try it, let me know if that works for you.

---

