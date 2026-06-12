---
title: "Backup/Restore failure, Networking /proc/net/dev permission denied"
date: 2009-05-28
forum: General Help
---

### Post by black_wolf on 2009-05-28
Earlier today I had a working Ubuntu 8.04 LTS system. I wanted to see if upgrading it to 8.10>9.04 would be worth it. To be safe, I backed up the system using a script similar to the one found here: [http://ubuntuforums.org/showthread.php?t=35087]("http://ubuntuforums.org/showthread.php?t=35087&highlight=clonezilla+tutorial")

```
tar cvpzf /backup/backup.tgz --exclude=/backup --exclude=/lost+found --exclude=/media --exclude=/mnt --exclude=/proc --exclude=/svn --exclude=/sys
```

I proceeded with the two updates without any problems. After restarting the system after the 9.04 update and testing it out, I decided that I'd be better off sticking with 8.04 LTS (call it an attachment).

In order to restore the system, I used a restore script similar to the one found along with the backup script above.

```
tar xvpfz /backup/backup.tgz -C /
```

Upon restarting the system and trying to log in I get this error in the ~/.xsession-errors file:

/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale-en_US.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit.d/default
/usr/bin/pulseaudio: unrecognized option '--start'
E: main.c: Failed to parse command line.
** (seahorse-agent:8919): DEBUG: This Gtk+ version doesn't have the GtkSetting::gtk-enable-input-sounds property.
** (seahorse-agent:8919): DEBUG: This Gtk+ version doesn't have the GtkSetting::gtk-enable-input-sounds property.
** Message: Another GPG agent already running


If I restart in recovery mode, using the root with networking, it fails to start networking. The error I'm receiving is:

/proc/net/dev: Permission denied.
Failed to bring up eth0.

Looking at the permissions for /proc/net/dev (something I did not backup and restore) gives -r--r--r-- 1 root root 0 2009-05-28 22:43 /proc/net/dev

Attempting to change the permissions to allow rwx doesn't stick after a reboot.

I realize this is a lot of detail, but I wasn't able to find anything searching. Does anyone have some ideas?

---

### Post by lavinog on 2009-05-28
I have to leave soon, but to answer part of your issue.
you did not need to backup /proc/...
The /proc/ folder is a special folder that is created when you boot.

the other problem is that it looks like you restored /etc over the new /etc
/etc is where the system configuration and startup scripts are...you will need to reinstall the os (not upgrade)
Save your backup though, after you reinstall the os, you should just restore your home folder.
I find the best way to restore the home folder is to restore it into an oldhome folder, and move files as needed...this gives me a way to tidy up my files.

---

### Post by black_wolf on 2009-05-28
After I updated to 9.04, I restored my backup from 8.04 - effectively overwritting anything not in the folders I excluded. Replacing /etc/ seems to me that it would be OK, as long as you replace whatever else it depended on (if I replaced /etc/ but not /bin/ then I could see your point).

I need to restore more than just my home directory - I'm looking to restore /etc/.

Would it be better (or at least a viable option) to reinstall 8.04 and then restore my backup over that installation?

---

### Post by lavinog on 2009-05-29
you could do that (reinstall 8.04 then restore)

---

### Post by lavinog on 2009-05-29
I usually backup /etc in a separate backup, and only use it for reference since some config files go through some major changes.
What in etc do you need to keep anyway?

---

### Post by black_wolf on 2009-05-29
I didn't set up this particular system, and if its possible to restore it to pre-upgrade, then I'd *much* rather do that then spend working hours re-installing Ubuntu, setting up user profiles, reconfiguring the svn, and setting up the software RAID that was in place.

If the software RAID actually sets up a new partition, then I don't have as much of a problem, although I can't be sure without looking at the partition table with a live cd. Do you know off the top of your head?

The most thing I'm concerned about is downtime - this installation hosts an SVN and backs up ~10 computers (I thought the backup I had would cover me, but apparently not unless I'm not restoring it correctly).

Is re-installing Ubuntu 8.04 the best/fastest way to get this system back up and running? If it is, then I'll get to it, just didn't want to unless I had no other option.

---

### Post by black_wolf on 2009-05-29
I've decided that the easiest thing to do at this point is to back up the config files I need from /etc/ and reinstall.

One question first though - I have a software RAID 5 setup using 3 of the 4 disks in the system (the first disk is the boot disk). Will I be able to mount the RAID array after I reinstall?

Thanks

---

