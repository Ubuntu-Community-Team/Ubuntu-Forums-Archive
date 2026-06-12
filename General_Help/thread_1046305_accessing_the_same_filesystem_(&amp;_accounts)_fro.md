---
title: "accessing the same filesystem (&amp; accounts) from different linux boots"
date: 2009-01-21
forum: General Help
---

### Post by v1nsai on 2009-01-21
I recently installed Fedora10 onto a 2gb partition on my hdd, pending me finding the solution to a small catastrophe on my ubuntu partition caused by some *ahem* disagreements caused by nvidia drivers.  Anyway, I kind of like Fedora and wouldn't mind learning my way around more than one linux OS, however I'm unable to do much since I can't find a way to tell Fedora to use the other partition for storing of downloads via yum (apt-get for fedora), storage for the desktop and home folder etc etc.

I'm sure there's a way to get the Fedora partition to use the home folder and storage on the Ubu partition, but I'm not sure how to do it and it makes for an awkward Google string.  Can anyone point me in the right direction for this, I'm sure its not too hard.

---

### Post by taurus on 2009-01-21
When you install Fedora, you can tell the installer to mount whichever partition that has your /home to /home but do not format it.  One thing you have to remember, Fedora creates a user with UID of 500 while Ubuntu uses 1000 for the first user so technically, you cannot use the same $HOME for Ubuntu & Fedora.  However, you can share the /home partition between the two though.  You can even use the same swap partition.

---

### Post by sedawk on 2009-01-21
And there is another problem - your home folder contains lots of
"invisible" dot-whatever directories like .mozilla and you might
have problems when running two different linuxes with different
versions of the same applications using the same .whatever directory
to store the configuration.
I recommend to use the same /home for both linuxes, but use
a different user. You can add them (manually) as 2nd user to the
other linux or (worst case) transfer files via the root account (sudo).

Otherwise it is totally okay to create a (logical partition) like
/export or /download or /music or whatever and then to mount it
from all installed linuxes! For write permission you should think
about putting all "writing" users to the same user group and make
the files and directories group writable.

---

### Post by vanadium on 2009-01-21
My approach to this would be

* Have all $HOMEs of the distro's on the root of the partition of the distro, in order to keep the application configuration data distro specific.

* Have a separate data partition for user documents.

* Assign a same user id to the same login on each distribution.

* Use symbolic links within the respective $HOME of each distribution to make the data on the separate data partition readily accessible.

In some cases, configuration data can be shared as well between distributions. This would apply to email for example. This can all be arranged using symbolic links.

---

### Post by timcredible on 2009-01-21
this is no problem, the only thing you have to do is make the same user accounts on each system have the same UID.  just because one starts with 500 and other starts with 1000 doesn't mean you can't create them with the same UID on both systems, just manually assign the UID when creating accounts.  when i do this, i call the first account that gets created at install time the same as the distro, like 'ubuntu', or 'fedora'.  then create the account(s) that will share /home with matching UIDs.  make /home it's own partition so that both distros use it as such, and you're all set.  if you're using the same window manager for both (like gnome), make sure it's the same version or you'll get weird gnome issues.  when i do this, i use gnome for one distro, kde for another, xfce for a third, which makes it much easier.

---

### Post by v1nsai on 2009-01-21
So all I need to mount is the home folder?  And that will work when I 'yum install' things and let me put things on my desktop right?  How exactly do I go about doing this?  I'm still kind of new to Linux filesystems and not sure how to make the right associations.

---

### Post by taurus on 2009-01-21
The command **yum install app** will not install apps to your desktop.  It will install apps to your / filesystem.

---

### Post by v1nsai on 2009-01-21
Yea I meant being able to yum install to the mounted drive and have items on my desktop go to the mounted drive sorry.

I ended up just reinstalling, I didn't have any terribly important data that didn't fit on my flash drive and it was becoming quite a pain.  I'd still like to know how to mount different filesystems though.  Is there a guide for this someone could point me to or anything?  I've tried a couple of different google searches but I'm just not sure how to word what I'm trying to do for a search engine.

---

### Post by v1nsai on 2009-01-22
bump.  Found a few forum posts but they're pretty vague, assuming knowledge of the filesystem and whatnot, I've been using ubuntu for a little while but I'm still kinda new, can anyone help me out?

---

### Post by vanadium on 2009-01-22
If the above is giving you trouble, I recommend you use one single distribution until you learned more about the gnu/linux system.  Do not run before you can walk.

---

### Post by v1nsai on 2009-01-22
You may be right, but I'm not worried about screwing anything up I keep what little data I "need" on a single flash drive, I got room to play. I could always reinstall and mount the partition when I do as Taurus suggested.  I'm a little unsure of how to make symbolic links work for this though, I understand them to be about the same as shortcuts in windows, yea? Anyway, all help appreciated.

---

### Post by vanadium on 2009-01-23
I am sorry, but if you want a complicated setup on the one hand, but need help with symbolic links on the other hand, we are missing something. Please post in the absolute beginners forum when appropriate.

---

### Post by v1nsai on 2009-02-03
*pffff* alright, I've looked over this a little more, I've gone over some really good guides on separating just the /home partition, but I'd rather configure user settings individually for each partition than mess with any funny gnome errors.

I tried creating symlinks to all my folders on sda2 and deleting all the folders except home on sda4 and replacing them with identically named symlinks, but THAT is not a good idea and I don't recommend it.  Grub error 26.  Don't understand why, but grub does not like it.

What I'm trying to do is run the operating system (with its own separate home folder) in one partition and use all the space on the other partition.  Can anyone point me in the right direction?

---

