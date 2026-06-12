---
title: "how to change default mount options for removalbe (vfat) devices?"
date: 2010-03-04
forum: Desktop Environments
---

### Post by akos.maroy on 2010-03-04
I want to change the default mount options for removable devices, especially vfat devices, to have shortname=lower instead of the default shortname=mixed mount option. I googled around, and found references to /system/storage/default_options/vfat/mount_options  gnome configuration option, but I don't seem to have this option set, actually, I don't seem to have a /system/storage tree in gconf-editor at all.

searching in gconf-editor doesn't really yield any results.

setting the above gconf setting doesn't help either.

any help would be appreciated...

---

### Post by poosterl on 2010-04-16
I'm struggling with the same problem. Have ever found a solution?

---

### Post by akos.maroy on 2010-04-16
> **poosterl said:**
> I'm struggling with the same problem. Have ever found a solution?

no, I haven't :(

---

### Post by retrocruizer rz899873214 on 2010-07-30
Hello,

found a way to change the default mount options when opening a USB-stick or simlar removable drive via gnome desktop under "location".

- Open commandline
- sudo gconf-editor
- open tree to syste,/storage/default_options

you will see some entries e.g. for ntfs or vfat.

- click on vfat and open key on right window.
- check new key and fill with the word noatime
- save this entry

Now we have the trouble to add a new directory e.g. for ext3, ext4 or the common word fuseblk used by gnome.

- leave gconf-editor
- go to your home-directory and you will have a ~/.gconf directory
- under this directory, you will find some structure comparable to the tree in gconf-editor. Therin are the  changed values apart from default.

- copy unter system/storage/devault_options the structure below vfat to ext3, ext4 and fuseblk

- reboot your maschine, because I didn´t found a way to force gconf-editor to reload this structure online

- back from reboot, open again gconf-editor unter (system/storage/default_options und you will now find the new structures unter ext3, ext4 and fuseblk
 
- edit the structure of vfat and add shortname=lower

- edit the structures of ext3 and ext4 to your needed options e.g. noatime, noadir, realtime and remove all others

- edit fuseblk to nosuid,nodev,allow_other,blksize=4096,relatime,noatime,nodiratime

This sets fuseblk to the defaults used before in gconf-editor with the additions of noatime, relatime and nodiratime.

fuseblk is used by my gnome to mount ext3 formatted usb-sticks.

Please be aware of the problems maybe resulting from using noatime, relatime and so on.

Kind reagrds
-mm-

---

### Post by lojack2374 on 2010-07-30
Like akos.maroy, I too do not have a /storage folder under /system
Nothing. Just:
  /dns_sd
  /gstreamer
  /http_proxy
  /proxy
  /smb

Running Ubuntu 10.04. Thoughts?


--
Chris

---

### Post by JustinR on 2010-07-30
> **retrocruizer rz899873214 said:**
> 
- sudo gconf-editor


FYI don't use sudo or gksudo on gconf-editor unless your actually using root as your user.

---

### Post by jasp1 on 2010-08-11
Like other above, I am running 10.04, and I do not have a system/storage/default_options in my gconf-editor window (running as myself or as root).

I too would like to change the option from "mixed" to "lower".

-Jay

---

### Post by bodmcn on 2011-04-23
It would be good to find an answer to this; I cannot find any references to the fact that the System/Storage has been removed in Ubuntu 10.04 (or before) or where these options now are.

All of the threads I have read have just stopped at the point where this comes up; can anyone shed any light on where these options now are in Ubuntu?

---

