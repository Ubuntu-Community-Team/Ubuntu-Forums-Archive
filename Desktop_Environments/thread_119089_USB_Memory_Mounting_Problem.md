---
title: "USB Memory Mounting Problem"
date: 2006-01-18
forum: Desktop Environments
---

### Post by gnuosphere on 2006-01-18
Hello,

I have installed a complete 5.10 Ubuntu network at my school. On the clients, when logged in as root, I can plug in a USB memory drive and it immediately pops up on the desktop - no problems.

However, when a NIS user is logged into a client and plugs in a USB memory drive, it fails to mount. "San Disk Cruzer Mini" (although it matters not what kind of stick is inserted - I have tried others) appears as an icon in "Computer - File Browser" but when I try to open it, I get the following message ...

"Mount Error
Unable to mount the selected volume
Error: Could not execute pmount"

Under "User Privileges" on the server, the user has "Enable access to external storage devices automatically" checked off so that can't be the problem. This is happening on every single one of the machines in the lab (all 15) so I know it is not a hardware problem.

Any ideas?

Thanks!

Peter
[http://gnuosphere.blogspot.com](http://gnuosphere.blogspot.com)

---

### Post by CzarAlex on 2006-01-18
I was told that this is a problem with the current version of KDE and is fixed in the next release. If needed, and if you still have gnome installed, you can mount it without incident under gnome until you update.

Hope it helps.

---

### Post by mer0090 on 2006-01-18
Hi,

I had the same problem and I have solved it going in the UserManager: enable "Show all users and groups", click on the properties of the user Hal, go in the tab of user privileges and enable "Enable access to external storage devices".

Hope it works.

Best,
Sebastiano

---

### Post by gnuosphere on 2006-01-19
Sorry I forgot to mention that we are using the Gnome desktop. So it seems to be a problem with both Gnome and KDE.

---

### Post by gnuosphere on 2006-01-19
mer0090,

thanks for the suggestion. Unfortunately, when I went to go check off the option under HAL, it was already checked off. I'm stuck!

---

### Post by gnuosphere on 2006-01-19
Whew! A student of mine (Hudson D.) just solved the problem. Seems so simple now. He logged in as root and changed the permissions on the pmount program (/usr/bin/pmount). He granted access to all and now the USB sticks mount when a NIS user is logged into a client.

---

### Post by casperl on 2006-01-25
I have the same problem and will fix it per this thread. 
Just to point out that I could mount all my USB devices without problems, until one day I plugged in a "San Disk Cruzer" reader for an MMC card.  
Since that plugin, only root can access USB mounted devices.  The same 'root only' privileges happened when accessing sound devices.  There is sound until I log in as a user.

I shall head home and restore sanity with user permissions, but surely there is a bug in the OS here?

---

