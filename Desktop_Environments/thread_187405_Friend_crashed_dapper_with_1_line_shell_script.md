---
title: "Friend crashed dapper with 1 line shell script"
date: 2006-06-02
forum: Desktop Environments
---

### Post by talz13 on 2006-06-02
So we were trying to get a smb share mounted on startup to the folder /home/xxxx/Desktop/Other

with the following command in the fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
//Other/E  /home/xxxxx/Desktop/Other  smbfs guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0
```
Now, when he reboots, it doesn't get mounted (i.e. the Other folder is empty).  He ran
```
sudo mount -a
```
it asked for the password, then completed.  Upon opening the Other folder again, it was properly mounted.

Since this was something that is going to need to happen every time, he made a shell script:
```
#!/bin/bash 
sudo mount -a
```
and attempted to run it.  He set it exec and ran it in the terminal, and after inputting his password, the machine was completely locked.  ctrl+alt+bs, ctrl+alt+del did nothing, and he had to use the reset button on the computer.



Something's definitely wrong here! (be it user error or otherwise) But I'd think that linux shouldn't crash from a possibly bad shell script!



We did check out the dmesg output, but there was nothing relating to smb or mounting other than the "mounting root filesystem" message.

---

### Post by talz13 on 2006-06-03
Does nobody have any input on this situation?  It's really quite strange, and I haven't seen it in the last year and a half that I've been on ubuntu (albeit, I haven't needed to mount a samba share TO ubuntu before)

---

### Post by pump on 2006-06-03
Try to add "auto".
Like this:
```
//Other/E  /home/xxxxx/Desktop/Other  smbfs guest,auto,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0
```

---

### Post by talz13 on 2006-06-03
[QUOTE=pump]Try to add "auto".
Like this:
```
//Other/E  /home/xxxxx/Desktop/Other  smbfs guest,auto,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0
```[/QUOTE]

Oh yeah!  It's been quite a while since I played with fstab, I forgot about auto...  That would probably explain why it wasn't auto-mounting, wouldn't it? :-P

---

