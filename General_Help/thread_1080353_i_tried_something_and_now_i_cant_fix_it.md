---
title: "i tried something and now i cant fix it"
date: 2009-02-25
forum: General Help
---

### Post by jamesnmandy on 2009-02-25
I tried adding two launch options to my USB hard drive in an attepmt to test a "fix" another user reported as working for them

here's the post from launchpad


> 
> This seems to be a duplicate of bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/119730/comments/82](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/119730/comments/82) And has nothing to do
> with usb transferrates but rather sata/harddisk transferrates. Setting "noatime,nodiratime" to the mount options in /etc/fstab solves the
> problem for me atleast.

noatime & nodiratime will not make any noticeable difference for the transfer of just 1 big file, and a lot of people here reported that symptom... Besides that the problem arises with non-ext volumes too.

I don't know if is just coincidence or luck, but I had this problem with my 64 bits system, I reinstalled Ubuntu and replaced with the 32 bits version and the problem is gone... Now I can achieve stable 10+ MB/s with my pen drive and 20+ MB/s with my usb sata disk.

Just in case it is useful:

$ uname -a
Linux vs-note 2.6.27-10-generic #1 SMP Fri Nov 21 12:00:22 UTC 2008 i686 GNU/Linux

so i right clicked on my USB hard drive (which is a SATA drive in a USB 2.0 enclosure), chose properties, went to launch options which was blank, and typed "noatime,nodiratime" without quotes of course but exactly like that

now i cannot mount that drive, says invalid launch options were specified, guessing maybe it's because this is a FAT32 hard drive and those are launch option commands only available for ext or whatever the linux filesystem is

how do i delete those launch options from the drive's properties now?  i cannot access the properties anymore, help!

and as a side note, is there anything else i can try to fix this horridly slow USB hard drive/device issue everyone is having?  

thanks#-o

---

### Post by Perryg on 2009-02-25
> **jamesnmandy said:**
> I tried adding two launch options to my USB hard drive in an attepmt to test a "fix" another user reported as working for them

here's the post from launchpad




so i right clicked on my USB hard drive (which is a SATA drive in a USB 2.0 enclosure), chose properties, went to launch options which was blank, and typed "noatime,nodiratime" without quotes of course but exactly like that

now i cannot mount that drive, says invalid launch options were specified, guessing maybe it's because this is a FAT32 hard drive and those are launch option commands only available for ext or whatever the linux filesystem is

how do i delete those launch options from the drive's properties now?  i cannot access the properties anymore, help!

and as a side note, is there anything else i can try to fix this horridly slow USB hard drive/device issue everyone is having?  

thanks#-o

Did you by chance make a backup of the fstab file before you edited it?
If not you still might be able to fix it by looking at the file and editing out the entries you made.

As for the speed issue I have no suggestions.

---

### Post by Blice on 2009-02-25
I'm not sure how to remove the launch options, but, in that quote above they were talking about editing the fstab (/etc/fstab), not the launch options.. You've unmounted it, unplugged it, plugged it back in, and the launch options weren't cleared?

Or did you edit the fstab? I'm confused.

---

### Post by jamesnmandy on 2009-02-25
sorry, yeah, i could not figure out how exactly where to put the entry in fstab, there was no mention of /dev/sdb1 in it so i didnt change it, i right clicked the icon for the removeable HDD and chose properties, then entered as above in the "launch options" field....didnt think about it being FAT32 and those being invalid options for that file system

my fstab file only shows the following (same as it was before i made the change in the drive properties)

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=2f77f082-0dc2-46a3-956b-4197e63883e8 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=44924d31-a31b-4af5-92d4-d389ffff2a1b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

and yes, after entering the commands in the launch options i unmounted the drive, then chose remount and get the error every time "invalid mount option when attempting to mount the volume", tried the obvious, unplug, reconnect, etc....it must have stored the launch options on a file on the drive that the OS uses when mounting it, but i cannot get into the file system on the drive to edit/remove it

---

### Post by Yellow Pasque on 2009-02-25
EDIT: follow heindsight's advice

---

### Post by heindsight on 2009-02-25
Open the GNOME configutation editor (should be in the menu at Applications>System Tools>Configuration Editor), or you can open a terminal and type:
```
gconf-editor
```
If you can't find it, you may need to install it  ```
sudo apt-get install gconf-editor
```
(I can't remember whether it's automatically installed by default).

Once you're in the configuration editor, navigate to system/storage/volumes there you should see something like _org_freedesktop_Hal_devices_volume_uuid_4871_2078 (in the left pane) select that, in the right pane you should then see a mount_options key with the value set to the mount options you specified. right click the mount_options key and select "Unset key".

---

### Post by jamesnmandy on 2009-02-25
> **heindsight said:**
> Open the GNOME configutation editor (should be in the menu at Applications>System Tools>Configuration Editor), or you can open a terminal and type:
```
gconf-editor
```
If you can't find it, you may need to install it  ```
sudo apt-get install gconf-editor
```
(I can't remember whether it's automatically installed by default).

Once you're in the configuration editor, navigate to system/storage/volumes there you should see something like _org_freedesktop_Hal_devices_volume_uuid_4871_2078 (in the left pane) select that, in the right pane you should then see a mount_options key with the value set to the mount options you specified. right click the mount_options key and select "Unset key".

thanks temujin for helping


:guitar:

thanks so much, worked perfectly, like editing a registry entry in the "previous OS"...LOL

now i just gotta find a work around or fix for the USB speed issues a lot of people are having, any insight on that topic?

---

### Post by heindsight on 2009-02-25
> **jamesnmandy said:**
> like editing a registry entry in the "previous OS"...LOL

I wouldn't know anything about that ;)

I don't much like gconf though, I much prefer good old flat text config files.

---

### Post by jamesnmandy on 2009-02-25
well if they dont fix the USB thing i will be forced to go back to the previous OS unfortunately, which is a shame, i dont want to, happy here, but having to wait 2 hours for a 7Gb file to transfer from one HDD to another is beyond reasonable when i could format this drive, install Windows 7 or Vista, transfer the file/s, format, and reinstall Ubuntu FASTER than i can simply transfer the file outright

thats a bold statement but it is 100% accurate and true

---

### Post by kgr132 on 2009-08-15
> **heindsight said:**
> Open the GNOME configutation editor (should be in the menu at Applications>System Tools>Configuration Editor), or you can open a terminal and type:
```
gconf-editor
```
If you can't find it, you may need to install it  ```
sudo apt-get install gconf-editor
```
(I can't remember whether it's automatically installed by default).

Once you're in the configuration editor, navigate to system/storage/volumes there you should see something like _org_freedesktop_Hal_devices_volume_uuid_4871_2078 (in the left pane) select that, in the right pane you should then see a mount_options key with the value set to the mount options you specified. right click the mount_options key and select "Unset key".

This did the trick for me. Thanks for posting.

---

