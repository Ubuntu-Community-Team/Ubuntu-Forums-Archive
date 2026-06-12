---
title: "Error: given UDI is not a mountable volume"
date: 2005-09-29
forum: Desktop Environments
---

### Post by mumushi on 2005-09-29
i just recieve this message after i downloaded and installed the new updates. i tried 30 new floopy disk and it displays the same message i also tried it on other boxes which has a floppy drive and also updated at this same day and it displays the same message i can't mount a floppy but i can format them. 

Can anyone please help me. What seemed to be wrong? Thanks in advance.

---

### Post by mumushi on 2005-09-29
in addition both boxes where i tried the floppy disks are both ubuntu. :D

---

### Post by graynotgrey on 2005-09-30
I have the same issue using Breezy on different machines (Dell and HP Pentium II and III towers). I can mount the drive from the command line with sudo but not via Nautilus. FSTAB is configured properly to mount the drive by users. A USB flash drive mounts automatically by itself, but the end users may ocassionaly want to use a floppy. I search Google and some issues relkated to HAL and the GNOME volume manager, but I did not see anything useful in terms of a end user resolving the issue.

---

### Post by mumushi on 2005-09-30
ok thanks for the tip. all i wanted is for me to mount my floppy.

---

### Post by Chandon on 2005-09-30
I'm running into this problem as well with a CD drive, although this should probably go in the Breezy forum.

---

### Post by DKschyper on 2005-10-02
I get this message too:
Error: given UDI is not a mountable volume.

Is there anybody there can help??:(

---

### Post by siah on 2005-10-18
Here is the bug report:
[http://bugzilla.ubuntu.com/show_bug.cgi?id=17562](http://bugzilla.ubuntu.com/show_bug.cgi?id=17562)

The workaround they suggest is manually mount the floppy 
e.g. `pmount  /media/floppy0`
If you like clicky things, you can make a launcher on the desktop that executes that command. Here's a copy of mine.

[siah-tibook:~] josiah% cat floppy.desktop 
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Exec=pmount /media/floppy0
TryExec=
Icon=/usr/share/pixmaps/gfloppy.xpm
X-GNOME-DocPath=
Terminal=false
Name[en]=open floppy
GenericName[en]=
Comment[en]=
[siah-tibook:~] josiah% ls -l floppy.desktop 
-rwx------  1 josiah  ome  215 18 Oct 01:14 floppy.desktop

---

### Post by zingibong on 2005-10-18
[QUOTE=siah]Here is the bug report:
[http://bugzilla.ubuntu.com/show_bug.cgi?id=17562](http://bugzilla.ubuntu.com/show_bug.cgi?id=17562)

The workaround they suggest is manually mount the floppy 
e.g. `pmount  /media/floppy0`
If you like clicky things, you can make a launcher on the desktop that executes that command. Here's a copy of mine.

[siah-tibook:~] josiah% cat floppy.desktop 
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Exec=pmount /media/floppy0
TryExec=
Icon=/usr/share/pixmaps/gfloppy.xpm
X-GNOME-DocPath=
Terminal=false
Name[en]=open floppy
GenericName[en]=
Comment[en]=
[siah-tibook:~] josiah% ls -l floppy.desktop 
-rwx------  1 josiah  ome  215 18 Oct 01:14 floppy.desktop[/QUOTE]

I typed *pmount /media/floppy0* and it spit out this:
*mount: I could not determine the filesystem type, and none was specified*
In my fstab the file type is set to *auto*

Any idea?

---

### Post by Xterminator on 2005-10-18
Try

```
ln -sf /usr/bin/pmount /usr/bin/pmount-hal
```

---

### Post by zingibong on 2005-10-19
[QUOTE=Xterminator]Try

```
ln -sf /usr/bin/pmount /usr/bin/pmount-hal
```[/QUOTE]

Unfortunately, did not help.
This time it says: 
*Error: could not determine real path of the device: No such file or directory*

Any more idea? :(

---

### Post by canadianwriterman on 2005-10-19
[QUOTE=siah]Here is the bug report:
[http://bugzilla.ubuntu.com/show_bug.cgi?id=17562](http://bugzilla.ubuntu.com/show_bug.cgi?id=17562)

The workaround they suggest is manually mount the floppy 
e.g. `pmount  /media/floppy0`
If you like clicky things, you can make a launcher on the desktop that executes that command. Here's a copy of mine.

[siah-tibook:~] josiah% cat floppy.desktop 
[Desktop Entry]
Encoding=UTF-8
Version=1.0
Type=Application
Exec=pmount /media/floppy0
TryExec=
Icon=/usr/share/pixmaps/gfloppy.xpm
X-GNOME-DocPath=
Terminal=false
Name[en]=open floppy
GenericName[en]=
Comment[en]=
[siah-tibook:~] josiah% ls -l floppy.desktop 
-rwx------  1 josiah  ome  215 18 Oct 01:14 floppy.desktop[/QUOTE]


What is "pmount" as opposed to "mount?"

---

### Post by bonjun on 2005-10-21
i have the same error too,,,
however, i can mount using 'pmount /media/floppy0' and can unmount from the launcher


[QUOTE=Xterminator]Try

```
ln -sf /usr/bin/pmount /usr/bin/pmount-hal
```[/QUOTE]

this one works for me...

---

### Post by paddyg on 2005-10-21
[QUOTE=zingibong]I typed *pmount /media/floppy0* and it spit out this:
*mount: I could not determine the filesystem type, and none was specified*
In my fstab the file type is set to *auto*

Any idea?[/QUOTE]

It didn't work because you have auto instead of vfat. It works with vfat.

But just take a look at ubuntu bugzilla, bug # 17562, comment # 17 (Oct 21) from martin pitt. A new pmount package has been prepared. Really hope the bug has been fixed.

---

### Post by Xterminator on 2005-10-22
Chage fstab to:

```
/dev/fd0        /media/floppy0   auto,vfat    rw,user,auto  0       0

```

---

