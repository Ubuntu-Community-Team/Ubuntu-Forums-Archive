---
title: "Annoying error when mounting NTFS partition."
date: 2009-01-31
forum: General Help
---

### Post by solwic on 2009-01-31
When I try to mount up my Windows partition I get this message:

[IMG]http://i444.photobucket.com/albums/qq165/joojoo612/Screenshot-1.png[/IMG]

I close the message and double click again, and it opens right up, no more trouble.  

Any reason why that happens?  I mean, it's not a big deal, but having to click the thing four times and clear an error message just to get into the NTFS partition is a bit annoying.  

Never had this problem before in Hardy - this is the first time I've mounted an NTFS partition in Ibex though, so it must be a new bug with 8.10.

Any help would be awesome.  Thanks!

---

### Post by solwic on 2009-01-31
Also, I have that Windows partition that I'd like to erase and put LinuxMint on it.  My /home for Ubuntu is on its own partition.  Can I install LinuxMint to the Windows partition and use my /home partition in both Ubuntu and Linux Mint?

---

### Post by taurus on 2009-01-31
You can use the same /home partition but not a good idea to use the same username for both distros.  Maybe on the Ubuntu, the username could be rock while the username in Mint could be rockie.

---

### Post by solwic on 2009-01-31
> **taurus said:**
> You can use the same /home partition but not a good idea to use the same username for both distros.  Maybe on the Ubuntu, the username could be rock while the username in Mint could be rockie.

Any reason why it's not a good idea?  I was thinking accessing something in, say, /home/james/Videos from Ubuntu and Mint.  

That's not a good idea?

---

### Post by taurus on 2009-01-31
Because the settings could be different between two distros.  However, you can access all the files on /home/rock if you log in as rockie (Mint) and vice versa as long as you have set the permissions to 755 for both accounts.

But if you want to use the same account for both distros, then that is your choice since nobody is going to stop you if you want to do that.

---

### Post by solwic on 2009-02-01
> **taurus said:**
> Because the settings could be different between two distros.  However, you can access all the files on /home/rock if you log in as rockie (Mint) and vice versa as long as you have set the permissions to 755 for both accounts.

But if you want to use the same account for both distros, then that is your choice since nobody is going to stop you if you want to do that.

Ah, the settings.  I forgot about that.  They're in folders like .mozilla-thunderbird, right?

How would I go about auto-mounting that /home partition when I boot, and calling it something like U-Home or whatever?  The Windows partition is 107.4GB, so plenty of room for its own /home.

---

### Post by taurus on 2009-02-01
The ~/.config, ~/.gconf, ~/.gconfd, ~/.gnome2, ~/.gnome2_private, etc.

If you want to use the same partition for /home, then just mount /dev/sda2 (or whichever the device is) to /home during the installing process except do not format it or all your data will be gone.

And if you don't want to use the same /home for both distros, then just add an entry in /etc/fstab and maybe mount it to /ubuntu_home or whatever mount point you want to use.

---

### Post by solwic on 2009-02-01
> **taurus said:**
> The ~/.config, ~/.gconf, ~/.gconfd, ~/.gnome2, ~/.gnome2_private, etc.

If you want to use the same partition for /home, then just mount /dev/sda2 (or whichever the device is) to /home during the installing process except do not format it or all your data will be gone.

And if you don't want to use the same /home for both distros, then just add an entry in /etc/fstab and maybe mount it to /ubuntu_home or whatever mount point you want to use.

You rock, dude.  Thanks a million.  :)

---

