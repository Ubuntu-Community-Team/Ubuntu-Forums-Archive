---
title: "Wrong file permissions: files from USB media"
date: 2007-05-09
forum: Desktop Environments
---

### Post by klausthorn on 2007-05-09
I administer two networks, in both users bring in files on their USB Stcks and cameras. While I'm glad that it works with ubuntu (as opposed to KDE on Fedora which we had before), the file permissions are constantly causing trouble: they are too restrictive, only the owning user has read and write permisisons. The co-workers are always blocked.

When the users get files from other linux or windows machines using scp, nfs or smb as method ("protocol") the system wide settings are honored:

1. set group as the "set group bit" of directories should
2. set read and write permissions for group and set read permissions for "others", as set in "umask=0002"

but when they retrieve the files form USB medium only the owner has permissions to read and write. It's not feasible to call the admin each time and unfortunately it is not feasible to teach them all how to change permsissions with nautilus. There are far too much new users each week to teach them all. Besides they would forget after a few days and it's not a "preference" that only some users want or need. All user need it constantly in the "honor parent dir permission and umask"-Setting. So: How can I change it globally, per ubuntu host?

thanks in advance for caring!

---

### Post by mlind on 2007-05-09
hiya, this might not work but it's worth a try

check out file /usr/share/gconf/schemas/gnome-mount.schemas:
```

<key>/schemas/system/storage/default_options/vfat/mount_options</key>
        <applyto>/system/storage/default_options/vfat/mount_options</applyto>
        <type>list</type>
        <list_type>string</list_type>
        <default>[shortname=mixed,uid=,utf8,**umask=077**,exec]</default>
.
.

```
These are systime-wide settings how gnome-mount will handle external FAT mediums, like USB sticks with FAT filesystem.

You can test this locally first, by editing local gconf key /system/storage/default_options/vfat.

---

### Post by jazzgossen on 2007-06-28
I just tried this solution. I commented out the old <default> line in /usr/share/gconf/schemas/gnome-mount.schemas, using <!-- --> syntax. Is that correct? And then I changed the default options to what I want. But when I open up gconf-editor as my local user, and navigate to /system/storage/default_options/vfat, the old defaults are still listed there. I could not find anything in ~/.gconf that should override the settings. Do I need to re-login or something for this to take effect?

---

### Post by mlind on 2007-06-28
> **jazzgossen said:**
> I just tried this solution. I commented out the old <default> line in /usr/share/gconf/schemas/gnome-mount.schemas, using <!-- --> syntax. Is that correct? And then I changed the default options to what I want. But when I open up gconf-editor as my local user, and navigate to /system/storage/default_options/vfat, the old defaults are still listed there. I could not find anything in ~/.gconf that should override the settings. Do I need to re-login or something for this to take effect?

yes, I guess you need to relogin. *kill -HUP $(pidof gconfd-2)* might work too.

---

### Post by jazzgossen on 2007-06-28
I just tried both logging out and logging back in, and killing my gconf-2. Is rebooting likely to help? I guess it shouldn't.

---

### Post by mlind on 2007-06-28
> **jazzgossen said:**
> I just tried both logging out and logging back in, and killing my gconf-2. Is rebooting likely to help? I guess it shouldn't.

There's a note about default schema locations in  /usr/share/doc/gconf2/README.Debian.
It seems that the file you need to edit is actually **/var/lib/gconf/defaults/%gconf-tree.xml **just search using the vfat keyword and you should find a similar list containing the default mount options.
After editing, killling the gdconfd-2 process makes it reload the schemas.

---

