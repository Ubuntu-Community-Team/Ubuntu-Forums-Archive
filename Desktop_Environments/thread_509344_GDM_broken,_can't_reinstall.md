---
title: "GDM broken, can't reinstall"
date: 2007-07-25
forum: Desktop Environments
---

### Post by stevehaines on 2007-07-25
Ubuntu 7.04 on an AMD 950 has broken GDM. At bootup, message is "Server authorization directory (daemon/ServAuthDir) is set to /var/lib/gdm but does not exist. Please correct GDM configuration and restart GDM."

At console, "gdmsetup" gives: Gtk-WARNING **: cannot open display"

"gdm-restart" and "gdm-safe-restart" produce "command not found."

Attempts to do a "sudo apt-get install gdm" or "sudo dpkg-reconfigure gdm" produce the error that says "Cannot lock the file: Are you root?"

I have tried as "sudo" and as "root" (I installed the root password): no luck.

Ubuntu is running in console mode, and will start an X Windown session with "startx".

Any ideas for recovering and re-configuring GDM? Thanks!

---

### Post by reckless2k2 on 2007-07-25
can you do a quick and dirty kdm install and use that?

---

### Post by stevehaines on 2007-07-25
No joy. Message says: " . . . /var/lib/dpkg/lock does not exist. Are you root?"

Yes, I'm root (the same result as a sudo user). I checked /var/lib, and there is no directory for either gdm or dpkg. It looks like I have no way to get anything from the repositories. Am I down to a complete reinstall of Ubuntu as the only option?

---

### Post by Mark_in_Hollywood on 2007-07-25
I've got the same or very similar problem.

Just before I rebooted a 2nd time after the desktop cd install, I got a balloon notification saying I had no disk space. I just ignored that:

next:

Next I did a re-start. Entered my user name and pw. up came: GDM could not write to your authorization file. This could mean that you are out of disk space (huh? just gave Gutsy ~40gig). I did get a notification balloon saying I was out of disk space, but thought that a "joke". Oooppss!

Put the alternate cd in the drive and booted to rescue. Answered questions and selected command line or shell ran fsck and was told that superblock last write time is in the future. I said Y to fix.

/dev/sda1 was not cleanly unmounted, check forced.
Pass 1: checking inodes, blocks and sizes
Pass 2: Checking directory structure
Pass 3: checking directory connectivity
Pass 4  checking reference counts
pass 5 checking group summary information
 /dev/sda1: ***** FILE SYSTEM WAS MODIFIED ***88
 /dev/sda1; ***** REBOOT LINUX *******
/dev/sda1: 209063/4505600 files (1.1% non-contigous) 2214419/9006432 blocks

---

### Post by stevehaines on 2007-07-25
The first failure gave me a message about a bad superblock. I booted Knoppix from a CD and ran fsck on the partition that has Ubuntu on it (hda5). A bunch of inode errors were reported, and I answered manually to have the program fix them. Now fsck reports that hda5 is clean (as well as hda3 with my /home directory, and hda 6 and hda7 with different Linux distributions on them.

But I seem to be dead in the water with Ubuntu if I can't get to a repository to reinstall GDM???

---

### Post by mannheim on 2007-07-26
> **stevehaines said:**
> No joy. Message says: " . . . /var/lib/dpkg/lock does not exist. Are you root?"

Yes, I'm root (the same result as a sudo user). I checked /var/lib, and there is no directory for either gdm or dpkg. It looks like I have no way to get anything from the repositories. Am I down to a complete reinstall of Ubuntu as the only option?

No package management stuff is going to run if you have lost the directory /var/lib/dpkg. I'm no expert here, but I think the key file in that directory is the file /var/lib/dpkg/status. The system keeps backup copies of that file as /var/backups/dpkg.status.* Check if those are still present on your system.

If those backup copies are there, you could try recreating the directory /var/lib/dpkg and then copying over one of the backups:

```
sudo cp /var/backups/dpkg.status.0 /var/lib/dpkg/status
```

---

### Post by stevehaines on 2007-07-26
Thanks Mannheim, I'll try that. For the present, here's what apparently worked:

As root, I made /var/lib/gdm. Then I wrote two files in /gdm with pico. ":0.Xauth" is a blank with nothing in it. ":0.Xservers" has a line of obscure code -- I copied it from the same file while running the Live CD. That got me my GDM sign-on screen back.

I copied the contents of /var/lib/apt and var/lib/dpkg to a memory stick. Then in XP I made a CD with that on it. Back in the broken Ubuntu I copied the contents into /var/lib/apt and /var/lib/dpkg. That restored apt and synaptic.

The last problem that I can see is that the "Hardware Abstraction Layer" is broken. I get that message when signing on. The system no longer finds the ZIP drive or the USB memory stick. Any ideas for that?

---

### Post by mannheim on 2007-07-27
If the package management is working again, have you tried reinstalling hal and related packages? Something like
```

sudo apt-get install --reinstall hal hal-info libhal1 libhal-storage1

```

---

