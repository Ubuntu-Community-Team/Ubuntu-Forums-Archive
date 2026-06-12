---
title: "rsync stops mid-transfer on large batches"
date: 2009-06-17
forum: General Help
---

### Post by zephyrcat on 2009-06-17
I have been using rsync to copy my home directory to an SD card. I recently got a Drobo+Droboshare (NAS) and want to do the same thing to the Drobo, but when I run rsync, it stops somewhere in .local and quits. This is the command I am using:

```
rsync -vz -rD --stats --delete --delete-excluded --exclude=".gvfs" --exclude=".VirtualBox" --exclude=".miro" --exclude=".nautilus" --exclude=".Trash" --exclude="*.iso" --exclude="*.ISO" --exclude=".dbus" /home/thomas/ backup.0/ >> ~/backupsh/home-drobo-log.txt

```

I also get these errors, but I don't think they are related:

```
rsync: mknod "/home/thomas/.gvfs/drobo on droboshare/Thomasm1530/home/backup.0/.dropbox/command_socket" failed: Function not implemented (38)
rsync: mknod "/home/thomas/.gvfs/drobo on droboshare/Thomasm1530/home/backup.0/.dropbox/iface_socket" failed: Function not implemented (38)
rsync: mknod "/home/thomas/.gvfs/drobo on droboshare/Thomasm1530/home/backup.0/.gdesklets/sockets/%3A0.0" failed: Function not implemented (38)
rsync: mknod "/home/thomas/.gvfs/drobo on droboshare/Thomasm1530/home/backup.0/.icedteaplugin/icedtea-appletviewer-to-plugin" failed: Function not implemented (38)
rsync: mknod "/home/thomas/.gvfs/drobo on droboshare/Thomasm1530/home/backup.0/.icedteaplugin/icedtea-plugin-to-appletviewer" failed: Function not implemented (38)
rsync: recv_generator: failed to stat "/home/thomas/.gvfs/drobo on droboshare/Thomasm1530/home/backup.0/.local/share/Trash/files/http:\\www.facebook.com\photo.php?pid=119209&id=1274271941.desktop": Invalid argument (22)
rsync: writefd_unbuffered failed to write 4 bytes [sender]: Broken pipe (32)
rsync: write failed on "/home/thomas/.gvfs/drobo on droboshare/Thomasm1530/home/backup.0/.local/share/Trash/files/issue24_en.pdf": Input/output error (5)
rsync error: error in file IO (code 11) at receiver.c(302) [receiver=3.0.5]
default_perms_for_dir: sys_acl_get_file(.local/share/Trash/files/Dropbox/Linux Loop/themetest1-drpbx/.bzr/repository, ACL_TYPE_DEFAULT): Input/output error, falling back on umask
rsync: recv_generator: mkdir "/home/thomas/.gvfs/drobo on droboshare/Thomasm1530/home/backup.0/.local/share/Trash/files/Dropbox/Linux Loop/themetest1-drpbx/.bzr/repository/obsolete_packs" failed: Input/output error (5)
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/home/thomas/.gvfs/drobo on droboshare/Thomasm1530/home/backup.0/.local/share/Trash/files/Dropbox/Linux Loop/themetest1-drpbx/.bzr/repository/packs" failed: Input/output error (5)
*** Skipping any contents from this failed directory ***
default_perms_for_dir: sys_acl_get_file(.local/share/Trash/files/Dropbox/Linux Loop/themetest1-drpbx, ACL_TYPE_DEFAULT): Input/output error, falling back on umask
rsync: recv_generator: mkdir "/home/thomas/.gvfs/drobo on droboshare/Thomasm1530/home/backup.0/.local/share/Trash/files/Dropbox/Linux Loop/themetest1-drpbx/style" failed: Input/output error (5)
*** Skipping any contents from this failed directory ***
default_perms_for_dir: sys_acl_get_file(.local/share/Trash/files/Dropbox, ACL_TYPE_DEFAULT): Input/output error, falling back on umask
rsync: recv_generator: mkdir "/home/thomas/.gvfs/drobo on droboshare/Thomasm1530/home/backup.0/.local/share/Trash/files/Dropbox/Photos" failed: Input/output error (5)
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/home/thomas/.gvfs/drobo on droboshare/Thomasm1530/home/backup.0/.local/share/Trash/files/Dropbox/Public" failed: Input/output error (5)
*** Skipping any contents from this failed directory ***
rsync: recv_generator: mkdir "/home/thomas/.gvfs/drobo on droboshare/Thomasm1530/home/backup.0/.local/share/Trash/files/Dropbox/WikiRacing" failed: Input/output error (5)
*** Skipping any contents from this failed directory ***
rsync: connection unexpectedly closed (37349 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(600) [sender=3.0.5]

```

The log is completely normal as far as I can tell, but it stops after copying some of the files in .local. Why does it just stop?

Thanks!

---

### Post by zephyrcat on 2009-06-19
Just to add some more info:

- It's not a a file size issue, since there should be ~500GB free on the NAS.
- What would cause rsync to stop in general?

---

### Post by zephyrcat on 2009-06-27
After waiting a few days, I posted this on the rsync mailing list as well. Again, no one responded.

Should I file this as a bug? I have a hard time thinking that it is really a bug, since I'm sure others have done much larger transfers before.

---

