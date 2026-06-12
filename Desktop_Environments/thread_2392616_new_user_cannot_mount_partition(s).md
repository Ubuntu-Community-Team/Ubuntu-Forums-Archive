---
title: "new user cannot mount partition(s)"
date: 2018-05-23
forum: Desktop Environments
---

### Post by harm54 on 2018-05-23
Hi,
On my ubuntu 16.04 system I created a new user but this new user cannot mount / access any of the already existing (and working) partitions.
I have been strugling with this for some time now, but am probably missing something obvious.
The disk (partition) icons are showing up in the menu bar.
Any clues?
Harm

---

### Post by TheFu on 2018-05-23
mounting storage requires sudo.  You can give full sudo rights or limited sudo rights just for specific commands.
The power to mount is the power to destroy, however.

There would be a few different methods to allow these rights, depending on what you need.

Update:
I should clarify.  There are different types of mounts with pros/cons for each.
Permanently connected storage (SATA/eSATA) should use the fstab method, but manual mount work for admins.
Network connected storage can use either the fstab or autofs or manual mounts.
Externally attached storage, like flash drives or USB connected storage can use autofs or gvfs.

So, in reality, any sort of storage can use almost any sort of mount method, but using gvfs to access permanent storage has so many downsides to make it a bad idea and shouldn't even be considered. GVFS is normally used through GUIs.  Often, users will get GVFS because that is what nautilus and other GUI file/network managers will use by default.  GVFS is slow and doesn't behave like "real mounts."  

A real mount modifies the /etc/mtab. gvfs does not.  This breaks lots of programs.
Real mounts don't have poor performance. gvfs performance is usually 40-70% slower.
Real mounts require root/sudo to make happen.
Real mounts make storage appear as though it is local to the system and end-users don't need to know anything more.
Real mounts work for all programs, regardless.  gvfs mounts only work for GUI tools that are aware of that type of mount, usually gnome tools.

If it isn't clear, I'm not a fan of gvfs.   There are times when I use it, like accessing my smartphone storage or quickly accessing SDHC or flash drives, but I won't use it for SSDs or spinning disks due to the poor performance. For external USB, but fast storage, I'll use autofs.  This is an 'as-needed' mounting technique.  It mounts storage when it is both connected AND actually requested.  That is ideal for an external USB3 HDD or networked NFS storage.

Sorry, I realize this is all probably overwhelming when you just want to point-click and have access to some flash drive.  On most Ubuntu systems, local users have authority to use gfvs from the file manager when they sit behind the physical machine.  If they remote into the system, that permission is withheld for security reasons.

So really, to be most helpful, we need to know which desktop environment, what sort of storage, how you want to mount it (permanent, temp, or quicky) and what level of skill you have, since some of these methods are 20 steps to setup, but *just work* after that.

After all that, never forget that Linux and all Unix-based systems are multiuser to the core.  That means file and directory permissions are used to control/allow access to different parts of the file system.  If the main userid (from the install) can access  and use the storage already, but the new userid cannot, it is likely just a permissions issue.  

Spending 45 minutes learning about permissions now will save you hours, days, weeks, months of frustration in the future.   Unix permissions are simple and elegant.  They behave the same regardless of whether you are local or remote, unlike some other OSes.  There are tutorials for this stuff.  Work through one of those, but also open a few terminals and play around with all the different permissions on your own until that "light bulb" goes off in your head to cement the understanding at least 2-3 times. 

Clear as mud?  Nobody knows this stuff initially. I put off really understanding permissions for about 6 months. Wish I hadn't.  In that time, my PC was hacked because I was ignorant.

---

### Post by yancek on 2018-05-23
> On my ubuntu 16.04 system I created a new user but this new user cannot mount / access any of the already existing (and working) partitions.

That is standard behavior on any Linux system since they are all created as multi-user systems.  The user created during the install of Ubuntu will have root privileges (using sudo), other users won't unless you manually set that up.  Generally, for a typical home computer user, there is no need to do this.  A secondary user will generally only have write access to the /home/user directory and sub-directories.  If you want to give other users access to other partitions you also need to manually configure that.

Take a look at post 6 at the link below which gives a basic explanation.

[https://ubuntuforums.org/showthread.php?t=1935435](https://ubuntuforums.org/showthread.php?t=1935435)

---

### Post by Skaperen on 2018-05-23
it is possible to configure a file system (in [FONT=courier new]/etc/fstab[/FONT]) to allow users to mount it.  or a device owned by other than root can be configured to allow the owner to mount it.  this is in addition to allowing selected (trusted) users to act as root via the _[FONT=courier new]sudo[/FONT]_ command (as configured in [FONT=courier new]/etc/sudoers[/FONT]).  man page documentation on these topics can help you do this if you really need to.

it is possible for an unprivileged user to do great harm to, or carefully take over, a system with the ability to do arbitrary mounts.  that's why it is normally limited to only the root user doing it.  _common practice_ is to have the usual system device(s) and home directory device automatically mounted at boot up time, and just left that way, whether a server or a desktop.

---

