---
title: "Fedora - not a happy experience"
date: 2007-12-19
forum: Fedora/RedHat and derivatives
---

### Post by desertboy on 2007-12-19
Been a Ubuntu user for some time now and am very comfortable with it, so I thought I might try Fedora 8.

On install it rewrote my grub, locked off access to my Ubuntu HD's which I couldn't get to boot from menu.lst, didn't recognize my network card (Which is an 8139, Ubuntu works fine and I think it has kernel support).

I had to blank the HD with fedora on it and reinstall grub from the livecd to get it working again. I would like to play around with another distro anyone recommend one that won't hose my system from the livecd.

I'm pretty certain it was fedora's LVM settings (I guess this is like dynamic disk's in Vista) causing the HD problems as from Ubuntu livecd I could see my Ubuntu drives not fedora and from fedora livecd I could see my fedora drive but not Ubuntu's.

Both saw my NTFS drive fine.

How can I install fedora to still be able to boot ubuntu and share files and how do I  get internet if I can't get my network card working.

This is all sort of a rhetorical question anyway as I think I shall probably try debian and gentoo instead.


Also fedora wouldn't let me

sudo gedit /boot/grub/menu.lst telling me my password was incorrect even though it was my root password setup from the administartion options in Gnome.

I didn't seem able to get root access, very annoying given Ubuntu just worked.

---

### Post by njparton on 2007-12-19
Opensuse 10.3 is worth a try if you're looking for variety.

---

### Post by Flyingjester on 2007-12-19
I don't believe sudo will work in fedora, there is actually a root user you can log into, should have set that up durring installation.

---

### Post by K.Mandla on 2007-12-19
Moved to Fedora/RedHat subforum. ;)

---

### Post by lynandal on 2007-12-19
puppy all the way.  saved my *** enough times, plus how can't you love the dog when it loads off your little 256 meg live cd.

:) ubuntu and puppy user. :)

---

### Post by Yoooder on 2007-12-19
If you're just beginning to venture into other Distros, give serious consideration to trying out an LiveCD/DVD versions or setting them up in a Virtual Machine first.

Each distro has its own quirks/quarks and practices--some will feel more like Ubuntu and some will feel pretty foreign to you.  The important thing is to try and understand why they are the way they are, each distro will target a slightly different market.

In any event don't put all your eggs in one basket, keep backups (or work in VMs) to prevent data loss, and most importantly HAVE FUN :)

Give Slackware, Debian, Gentoo, Fedora, and the rest of the major distro's a chance--maybe even some of the BSD flavors and Solaris.

---

### Post by desertboy on 2007-12-19
I set it up in a VM and internet worked fine and of course it didn't hose my grub.

I had high hopes for fedora and I might play around a bit more, my lesson really is don't use my "production machine" for experimenting with OS's and there's no substitute for a installing on a real machine.

---

### Post by jinx099 on 2007-12-19
You can use sudo in Fedora, you just have to set it up manually.  Do this:
```

sudoedit /etc/sudoers

```

Add your user, or group to the file and you now have sudo just like Ubuntu.

---

### Post by igknighted on 2007-12-19
> **desertboy said:**
> Been a Ubuntu user for some time now and am very comfortable with it, so I thought I might try Fedora 8.

On install it rewrote my grub, locked off access to my Ubuntu HD's which I couldn't get to boot from menu.lst, didn't recognize my network card (Which is an 8139, Ubuntu works fine and I think it has kernel support).

I had to blank the HD with fedora on it and reinstall grub from the livecd to get it working again. I would like to play around with another distro anyone recommend one that won't hose my system from the livecd.

I'm pretty certain it was fedora's LVM settings (I guess this is like dynamic disk's in Vista) causing the HD problems as from Ubuntu livecd I could see my Ubuntu drives not fedora and from fedora livecd I could see my fedora drive but not Ubuntu's.

Both saw my NTFS drive fine.

How can I install fedora to still be able to boot ubuntu and share files and how do I  get internet if I can't get my network card working.

This is all sort of a rhetorical question anyway as I think I shall probably try debian and gentoo instead.


Also fedora wouldn't let me

sudo gedit /boot/grub/menu.lst telling me my password was incorrect even though it was my root password setup from the administartion options in Gnome.

I didn't seem able to get root access, very annoying given Ubuntu just worked.

Sounds like you rushed in without doing research.  A few suggestions that may make your experience better if you were to try again:

1) Fedora does not use "sudo" by default.  In fact, I think Ubuntu may be the only distro that does.  To get root access you need to switch to the root user (typing the command 'su -' accomplishes this).

2) If you really prefer sudo, you can enable it by uncommenting the appropriately labeled line in /etc/sudoers.  You then need to add your user to the group called wheel.  After logging out and back in you should be able to use sudo like in Ubuntu (although to get access to all the commands you need to modify your path, as Fedora does not give the local users access to everything by default... if you really want to go this far see fedoraforums.org)

3) Check out the distro which you are trying's forums.  For fedora, the primary forums are a [http://fedoraforum.org](http://fedoraforum.org).

4) Is that a wireless or a wired nic?  Not sure why a wired nic would not work... perhaps a bad burn?  I cannot think of any reason for it at least.  I would post this at fedoraforum.org if you want a solution.

5) Using root access, you could have modified the menu.lst file to get to get Ubuntu to boot.  Since you didn't know how, an alternative method (re-installing Ubuntu's grub, it would have found Fedora's) could be found here: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub).

6) To mount Ubuntu's partitions, you need to manually mount them (if you did not set mount-points at install time).  To do this, you need to identify the partition name (as root), by typing 'fdisk -l'.  Then using the mount command (mount /dev/partition /mount/point).  You could also add that mount point and partition to the /etc/fstab file to have it automatically mount every time.

7) I would avoid LVMs if you get the chance again.  They are really neat and allow you to do some great things (single volumes spanning multiple drives, for instance), but unless you have a need, they are often more trouble than they are worth.

8) Mentioned it before, but research the distro you are trying before you use it.  You would/could have run into almost all of these problems with any distro.  I would highly recommend reading all the literature and forums before installing (especially for distro's like gentoo... in fact I would print the 60+ page manual before installing that one :P) so nothing surprising comes up.

Hope this helps, good luck trying distro's!

---

### Post by elithrar on 2007-12-26
> **Flyingjester said:**
> I don't believe sudo will work in fedora, there is actually a root user you can log into, should have set that up durring installation.

Alternatively:
```

$ su - 

```

It'll prompt for your password and then:
```

# echo 'yourusernamehere ALL=(ALL) ALL’ >> /etc/sudoers

```

Now you can use sudo as you would in Ubuntu or similar (eg. sudo yum install firefox)

---

