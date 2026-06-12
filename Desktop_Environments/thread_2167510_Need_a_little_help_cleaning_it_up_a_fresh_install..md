---
title: "Need a little help cleaning it up a fresh install."
date: 2013-08-13
forum: Desktop Environments
---

### Post by scott7 on 2013-08-13
I just installed ubuntu12.04 on a Asus EEE Pc 901. Well bad thing is it only has a 4gig hard and 2nd hard of 16gig. Sure I could have installed it on the 2nd but I was hoping to install it on the 4gig as it is 4x faster then the 16gig.


My question/story is 
I went to do a update and it needs 500mb of space but only 300mb left. So I thought why not use software center to remove the stuff that this eee pc wont ever use. But the bad part is I removed it but it increased in size usage. Sure the apps are not on the list but the diskspace increased rather then decrease. I was wondering is there a way I can clean this up to make more room. 

I used the following already.

sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove

It cleaned up a hole 12mb.

If anyone knows how I can cleanup more please do share.

---

### Post by ibjsb4 on 2013-08-14
Check out the desktop package list.

[http://packages.ubuntu.com/precise/ubuntu-desktop](http://packages.ubuntu.com/precise/ubuntu-desktop)

You must have everything in red.  Everything in green are recommended packages and not necessary for the desktop to function.

---

### Post by scott7 on 2013-08-14
Thanks for the list. But I was hoping someone could help me or tell me some of the big thigns that are not really used at all that I can removed.

---

### Post by ibjsb4 on 2013-08-14
Give me a few to come up with a list :)

---

### Post by ibjsb4 on 2013-08-14
[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter (copy and paste):

```
sudo apt-get remove --purge apport-gtk bluez bluez-cups bluez-alsa bluez-gstreamer brasero britty cups cups-bsd cups-client deja-dup empathy fonts-kacst-one fonts-khmeros-core fonts-lao fonts-nanum fonts-takao-phothic fonts-thai-tlwg gcc gnome-bluetooth gnome-disk-utility gnome-orca gnome-screensaver gnome-sudoku gwibber hplip libreoffice-calc libreoffice-gnome libreoffice-help-en-us libreoffice-impress libreoffice-math libreoffice-style-human ubuntu-docs
```

There is more that can be removed, see what this will free up.

Also, this is untried by me and should not bork your system, but no guarantees.

EDIT:  I forgot.  Follow that with an  apt-get autoremove

---

### Post by scott7 on 2013-08-14
I guess that will do for now down to 400mb now of space on it. If push comes to shove I can just tos 13.04 on the 16gig if it becomes a issue.

---

### Post by 3rdalbum on 2013-08-14
> **scott7 said:**
> I guess that will do for now down to 400mb now of space on it. If push comes to shove I can just tos 13.04 on the 16gig if it becomes a issue.

4 gigabytes of disk space is far too small for any *buntu. You should use the 16 gig for the operating system otherwise you will only have a tiny amount of space for programs. Programs must be installed on the same partition as the operating system.

---

### Post by ibjsb4 on 2013-08-14
Its easier/better to build than take apart

[http://www.ubuntu-mini-remix.org/](http://www.ubuntu-mini-remix.org/)

This is a text only (no GUI) install, but this way you could add ubuntu without the recommended packages with one command.

```
sudo apt-get install --no-install-recommends ubuntu-desktop
```

I don't know what size the final install will be, never tried it this way.  I do 'roll my own' and the install Im on right now is 2.5GB.

Good luck and welcome to the forums :)

---

### Post by oldos2er on 2013-08-14
The minimum hard disk space for desktop Ubuntu is 5GB: [https://help.ubuntu.com/lts/installation-guide/amd64/minimum-hardware-reqts.html](https://help.ubuntu.com/lts/installation-guide/amd64/minimum-hardware-reqts.html)

I agree with 3rdalbum that, unless you want to do without any graphical interface, install Ubuntu to your 16GB drive.

---

