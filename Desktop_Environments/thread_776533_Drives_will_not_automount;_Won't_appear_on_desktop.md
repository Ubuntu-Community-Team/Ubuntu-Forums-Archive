---
title: "Drives will not automount; Won't appear on desktop"
date: 2008-04-30
forum: Desktop Environments
---

### Post by TheAlbinoEthiopian on 2008-04-30
I accidentally clicked "allow xfce to manage the desktop" in the desktop settings, and when I checked it back, the only things that reappeared on my desktop were File System and Trash, my Home folder, my slave drive, and my USB drive disappeared, and became unmounted.  When I restart, the desktop is the same and nothing plugged in automounts.  When I unplug and plug my USB drive back in, it mounts, but still doesn't appear on the desktop.  I've only been using Xubuntu for about a month now, so I'm still learning, can anyone shed some light as to what's going on here?  Thanks in advance.

---

### Post by Person98 on 2008-04-30
i noticed a similar thing when i upgraded to hardy, it used to work fine in gutsy, but i also haven't done a fresh install so i don't know if it broke during the upgrade process. my 2 other internal harddrives don't appear on the desktop, or in thunar, however they appear in nautilus, i can still see my floppy drive and home folder though. it is rather annoying to boot up nautilis every time i want to access another drive

---

### Post by dale_nx26 on 2008-04-30
I had this problem too. I wanted to automount my NTFS partition (where my music is stored), and I discovered that by setting the Storage Device Manager, I can configure the drives to do. Well...at least that's how I remembered doing it. I don't know if it involves using GParted.

Also, for USB drives, for me, it seems like they don't mount because maybe they're not formatted (any type) yet. After I formatted them, they mount. So check that.

---

### Post by T-Virus on 2008-05-01
Maybe you lack package like **autofs** for automounting all the stuff?

---

### Post by mali2297 on 2008-05-01
In Thunar, go to **Edit -> Preferences -> Advanced -> Volume Management** and perhaps change some setting.

---

### Post by denham2010 on 2008-05-02
I have a similar but not as severe issue.

My internal drive is split into 4 partitions:

    /
    /home
    /media/Files
    swap

In Gutsy, my desktop would display Home, File System ( / ) and Files ( /media/Files ).

After the upgrade to Hardy, Files is no longer displayed on the desktop. It does automount, it just doesn't display on the desktop.

When I plug in usb devices, they all automount and appear on the desktop, so I'm a little confused as to what has happened here.

It's not a big isue though. I just created a link on my desktop to access it easily, but would be interested if anyone has a fix......

One thought, when I had Feisty, entries in fstab had to mount to /mnt to display on the desktop, while entries mounting to /media did not display on the desktop.

With Gutsy, this changed to /media displaying and /mnt not (the result being I had to create a link from /media to /mnt so my Amarok music database would not have to be totally re-written)

I am wondering if with Hardy, this has changed back again? But then again, usb devices are displaying and they mount to /media....

Go figure.....Thoughts anyone?

---

