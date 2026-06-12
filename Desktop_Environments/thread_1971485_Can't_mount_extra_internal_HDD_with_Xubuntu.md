---
title: "Can't mount extra internal HDD with Xubuntu"
date: 2012-05-02
forum: Desktop Environments
---

### Post by M_Mynaardt on 2012-05-02
Hi!

This is something I just cannot seem to figure out on my own this one is!  :(

My computer runs on Xubuntu (12.04 now) and I have an old hard drive from my previous PC installed internally.  Waste not want not, eh?  Before I got hooked on Xfce (and Xubuntu), I ran Mint 10 with Gnome.  Mint would automatically detect my extra hard drive and allow me to mount and unmount the extra disk with a right click on its icon on the desktop or the Nautilus file manager.  But such is not the case with Xubuntu.

I have had advice on how to be able to mount and unmount this extra drive by making appropriate changes to the **/etc/fstab** file.  I've been trying this today as many different ways as I can think of with the little knowledge I have on these weighty matters.  The results are always the same: the disk is *sort of* present, and I can even mount it.  ***However***, I cannot actually _save_ files to it!  This is inconvenient for a drive I'd like to use for backing up data!  :P

What I _want_ to have is a drive icon for this extra internal drive showing up on my desktop and Thunar so I can mount and unmount the drive with the ever-handy right click from the desktop any time I want.  Much like I was able to do with Mint 10.  I'm trying to make things work properly in the **/etc/fstab** file, which would have been created when I first installed Xubuntu 11.10 on my PC last year.

I _think_ I'm not using **mkdir** properly to make a mount point.  I tried to use this to make a mount point:
```
# mkdir -m 777 /mnt/sparedrive
```
This did make the directory /mnt/sparedrive, but it does not seem to have the proper permissions when I try to access my extra drive using this as a mounting point.  Am I therefore using the **mkdir** command wrong?

I'm also not 100% sure if I'm making changes properly in **/etc/fstab**.  Here is what I tried:
```
/dev/sda1   /mnt/sparedrive   ext4   rw,exec,noauto,user,sync   0 0
```
This *sort of* works.  I can mount the drive, but then I can't actually write anything to it.  I'm not sure if it's because I didn't use **mkdir** properly.

I also like to be able to make use of the  floppy drive in this *ageing* computer of mine.  It just won't work.  If I insert a disk, I can hear *something* happening with the drive.  But it just won't mount.  It's not a big deal in this age of flash drives.  But it would be nice if I could make use of the gear I have on this old machine.  This is the **/etc/fstab** line for my floppy drive:
```
/dev/fd0    /media/floppy0    auto    rw,user,noauto,exec,utf8    0  0
```

If someone could help me with these posers, especially mounting the extra internal hard drive, I'd be ***ever so grateful!***  :D

I'm sure I have most of the pieces of this puzzle.  But I'm just having troubles putting them together properly.

Thanks in advance, if someone can help me with this one!

---

### Post by Jose Catre-Vandis on 2012-05-02
For the second HDD this is what I would do:
```
sudo mkdir /mnt/sparedrive
```
(although I usually use the /media folder)

```
sudo blkid
```
This will give you output and the UUID for your second HDD

```
sudo nano /etc/fstab
``` add the lines

```
#sparedrive
UUID=xxxxxxxxxxxxxxx   /mnt/sparedrive   ext4    defaults  0  0
```

Reboot

**sparedrive** should be there in thunar.

Next:

```
sudo thunar
```to run thunar as root

If you go Filesystem > mnt then right click on sparedrive > properties > permissions to change permission for all the files and folder in the drive.

Alternatively, you could do this from a terminal:
```
sudo chmod -R 0777 /mnt/sparedrive
```

HTH

Can't help with the floppy, forgotten all about them ;)

---

### Post by M_Mynaardt on 2012-05-02
I ***finally*** got the old hard drive working.
\\:D/

Not quite as I would've liked, but it's a huge step forward!

I had to have a couple of tries at it, mind you!  I first tried to edit **/etc/fstab** and then change the permissions of **/mnt/sparedrive**.  But that was a failure.  So, I tried it again.  This time, I changed the permissions of **/mnt/sparedrive** and _then_ edited **/etc/fstab**.

Then I rebooted it and it worked.

I would have preferred to be able to right click a hard drive icon for the spare drive icon on the desktop to mount/unmount as I saw fit.  Which is how it worked under Gnome some time back.  But, oh well.  At least I have access to it now.

There isn't an icon showing up on either the desktop nor Thunar for the drive itself.  Even thought I can access the old drive via **/mnt/sparedrive**.  I therefore created a separate desktop icon sort of thing with a silly Tux on a hard drive to open **/mnt/sparedrive**.  Just as a bit of a short cut.

This was a chore!  Next computer I get will have ONE internal drive, and I'll get an external multiple bay hard drive enclosure to toss in my old hard drives to use as extra back up storage.  At least Xubuntu is no muss no fuss with external USB hard drives being plugged in!

I did try messing about, a bit, with the floppy drive.  I changed the permissions on /media/floppy0, just as I did with /mnt/sparedrive.  But that didn't work.  Oh well.   I did make considerable progress!

Anyway, thank you so much for the advice, Jose Catre-Vandis!

:guitar:

---

### Post by M_Mynaardt on 2012-05-02
Now that I feel a bit better about messing about with **/etc/fstab**, would anyone know how I might be able to configure things so that instead of my old drive always auto mounting, I would have an icon for the spare drive on my desktop and in Thunar?

When I used Ubuntu 10.04 and Mint 10, both with Gnome, that was set up automatically for me.  There was a hard drive icon for the spare drive in both Nautilus and the desktop.  I could then right click said icon to mount and unmount the drive as I pleased.

I'm **very** excited that I can now access this old hard drive after months of not being able to do anything with it.

But I'd also like to see if I can learn a bit more about this fancy geek stuff too.

Still, no complaints!  I had no success with this hard drive at all until I followed the advice of Jose Catre-Vandis.

I figure it's a good day indeed if I make progress with some Linux nitty-gritty!
8)

---

### Post by Jose Catre-Vandis on 2012-05-03
Not sure if you are getting the word "mount" confused with "open".

If you really only want to "mount" the drive when you want to you could set up a launcher with this command:
```
gksudo mount /dev/sda1 /mnt/sparedrive
``` and depending on your settings thunar will open up a window.
(you'll have to comment out the line in fstab to stop it automounting).

You could write a little bash script that would check whether the drive is mounted or not and mount it / unmount it accordingly

I'm guessing the old HDD wasn't in the machine when you installed, which is why you are not getting everything happening automagically. If you did a fresh install with the old HDD installed/attached, xubuntu and thunar should automatically find it and mount it.

You can also (when in thunar) drag the directory icon for /mnt/sparedrive across to the sidepane (if you are using sidepane view)

---

### Post by mips on 2012-05-03
Have you tried generating a UUID for the drive which appears in the fstab with the right settings/permissions? Should work...

[https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[http://www.cyberciti.biz/faq/linux-finding-using-uuids-to-update-fstab/](http://www.cyberciti.biz/faq/linux-finding-using-uuids-to-update-fstab/)

---

### Post by M_Mynaardt on 2012-05-03
> **Jose Catre-Vandis said:**
> Not sure if you are getting the word "mount" confused with "open".

If you really only want to "mount" the drive when you want to you could set up a launcher with this command:
```
gksudo mount /dev/sda1 /mnt/sparedrive
``` and depending on your settings thunar will open up a window.
(you'll have to comment out the line in fstab to stop it automounting).

You could write a little bash script that would check whether the drive is mounted or not and mount it / unmount it accordingly

I'm guessing the old HDD wasn't in the machine when you installed, which is why you are not getting everything happening automagically. If you did a fresh install with the old HDD installed/attached, xubuntu and thunar should automatically find it and mount it.

You can also (when in thunar) drag the directory icon for /mnt/sparedrive across to the sidepane (if you are using sidepane view)

I'll try checking that out and see how it goes.  Thanks.

Yes, the extra HDD was an afterthought.  My late PC died just after I'd had two brand new hard drives installed.  And since I sometimes could teach a certain E Scrooge a thing or two about being cheap, I kept those two drives.  I had one put in an external casing that works just fine with a USB connection.  The other one I had someone install in my then new computer as an after thought.

Before installing Xubuntu on my computer,  Gnome-based Linux made it much easier to access that drive.

Oh well, this is the DIY way of learning things, eh?

---

### Post by M_Mynaardt on 2012-05-03
> **mips said:**
> Have you tried generating a UUID for the drive which appears in the fstab with the right settings/permissions? Should work...

[https://help.ubuntu.com/community/UsingUUID](https://help.ubuntu.com/community/UsingUUID)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[http://www.cyberciti.biz/faq/linux-finding-using-uuids-to-update-fstab/](http://www.cyberciti.biz/faq/linux-finding-using-uuids-to-update-fstab/)

I got the UUID for the spare drive working fine.  I just need to fine tune it a bit for getting icons and such.

---

### Post by M_Mynaardt on 2012-05-03
> **Jose Catre-Vandis said:**
> Not sure if you are getting the word "mount" confused with "open".
(etc, etc ...)


Actually, I just might be getting those confused.

I just assumed that "mount" meant to switch a drive on.  Are there important differences to those terms in Linux?  There probably is, I'm sure.

---

### Post by M_Mynaardt on 2012-05-03
**Oh ... Heck!**
:mad:

I found out that the floppy drive I was whining about was working the entire time!

I kept getting indications it wasn't mounted.

***However***, if I insert a floppy disk into the drive and use Thunar to open **/media/floppy0** (the mount-point designated in **/etc/fstab**), then ... ***There it is!***

Oh well; better late than never for finding out these things, eh?

I made a symbolic link to /media/floppy0; **~/.dev-floppy** (just because)

I then created a little desktop icon, therefore to open the floppy with:
```
[Desktop Entry]
Encoding=UTF-8
Name=Floppy
Comment=Access a floppy drive, if one's inserted
Icon=/home/user/.extra-icons/floppy-blue-1.png
Exec=/usr/bin/thunar "/home/user/.dev-floppy"
Terminal=false
Type=Application

```

It works, anyway.  Funny that the floppy drive never shows as mounted, even when there's a disk in it!

---

