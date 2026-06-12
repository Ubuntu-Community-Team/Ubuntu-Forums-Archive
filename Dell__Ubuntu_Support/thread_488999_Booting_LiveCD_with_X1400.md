---
title: "Booting LiveCD with X1400?"
date: 2007-06-30
forum: Dell  Ubuntu Support
---

### Post by RangerDanger on 2007-06-30
I am new to Linux and am wanting to use ubuntu.  I have read about the problems that ubuntu has with ati Xseries cards.  I have read all the solutions and none work without being able to boot and get wireless working so that files can be updated.  Will ubuntu being releasing an updated LiveCD with a fix?  I have tried many other distros and they all boot fine.

---

### Post by neptho on 2007-06-30
You're unlikely to see a fix specifically for those of us with ATI cards at least until the release of Gusty.

It's fairly easy to make it work with Feisty, however.  When you go to install, and it crashes out, login,  and run the following:

```
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
```

Then, restart X with:

```
sudo /etc/init.d/gdm stop; sudo /etc/init.d/gdm start
```

Finally, after you install everything and reboot into Ubuntu, it will have a problem again, since you were running from a RAM disk.  Rerun the whole thing again:

```
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
```

Then, restart X with:

```
sudo /etc/init.d/gdm stop; sudo /etc/init.d/gdm start
```

You're setup with Ubuntu, and shouldn't have any issues from this point forward.  (Kubuntu users, replace 'gdm' with 'kdm' above.)

---

### Post by RangerDanger on 2007-06-30
I know this all already and it does not work without a network connection and I have no idea how to get a network connection without booting up all the way.  I tried out pclinuxos and it configures the wireless first it would be nice if ubuntu did this as well.  I have no idea how to get the network up to get the updates.


> **neptho said:**
> You're unlikely to see a fix specifically for those of us with ATI cards at least until the release of Gusty.

It's fairly easy to make it work with Feisty, however.  When you go to install, and it crashes out, login,  and run the following:

```
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
```

Then, restart X with:

```
sudo /etc/init.d/gdm stop; sudo /etc/init.d/gdm start
```

Finally, after you install everything and reboot into Ubuntu, it will have a problem again, since you were running from a RAM disk.  Rerun the whole thing again:

```
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
```

Then, restart X with:

```
sudo /etc/init.d/gdm stop; sudo /etc/init.d/gdm start
```

You're setup with Ubuntu, and shouldn't have any issues from this point forward.  (Kubuntu users, replace 'gdm' with 'kdm' above.)

---

### Post by radeon21 on 2007-07-01
is there any way for you to use a wired connection?  that would be the easiest way

or, if you just want to get to any sort of display, you can use the generic vesa driver.  what you need to do is (in the terminal) type:

```

sudo nano /etc/X11/xorg.conf
```

and then edit the section under devices by changing 'ati' to 'vesa'

alternately, you can type into the terminal:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

and select the vesa driver when it asks you for screen resolutions, driver info, etc.

good luck!

---

### Post by neptho on 2007-07-01
> **RangerDanger said:**
> I know this all already and it does not work without a network connection and I have no idea how to get a network connection without booting up all the way.  I tried out pclinuxos and it configures the wireless first it would be nice if ubuntu did this as well.  I have no idea how to get the network up to get the updates.

Try 
```
%sudo -c 'echo "deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070417)]/ feisty main
restricted"' >> /etc/apt/source.list'
```

before you run the second installation of fglrx; it should pull it from the CDROM.

---

### Post by RangerDanger on 2007-07-02
Wow I know so little, but am getting the idea.  I have so much to learn.  I will take all this advice and see what happens.  On a side note, are there any good current books out there that would give me a good overview of linux?  I went to the book store and there were so many, but most were so specific or about a certain distro.

---

### Post by neptho on 2007-07-02
That's one of the problems with Linux - there are a million different distributions of it, and few are alike.  However, Ubuntu is Debian based, and still uses many of the Debian tools (apt-get, et al), so it can't hurt.

When you install, you can install the Ubuntu documentation (ubuntu-docs), and [this looks quite useful](http://www.ubuntuguide.org/).

There will be many differences, but [this tutorial](http://www.debian.org/doc/manuals/debian-tutorial/) (for Debian) will also provide usefulness, such as X won't start and you need to get around, various locations of many tools (Ubuntu still shares many of these paths), et al.

Good luck, and welcome to Ubuntu!

---

