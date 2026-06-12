---
title: "Captive-ntfs &amp; cdfs"
date: 2005-06-21
forum: Desktop Environments
---

### Post by Dave_is_sexy on 2005-06-21
... are going to be awesome.

But neither work. No idea why really, but at boot up, when all the mounted things get listed it is not there. 

Here is my fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda7       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /boot           ext3    defaults        0       2
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda6        /mnt/cache  ntfs    ro,user,auto,umask=0222  0       0
/dev/hda2        /mnt/win2k  ntfs    ro,user,auto,umask=0222  0       0
/dev/hda5        /mnt/winxp  ntfs    ro,user,auto,umask=0222  0       0
/dev/hdb1        /mnt/data  ntfs    ro,user,auto,umask=0222  0       0
/dev/hdc        /media/cdfs   cdfs	ro,user,noauto  0       0

/dev/hda2 /mnt/x-win2k captive-ntfs defaults,noauto 0 0
/dev/hda5 /mnt/x-winxp captive-ntfs defaults,noauto 0 0
/dev/hda6 /mnt/x-cache captive-ntfs defaults,auto 0 0
/dev/hdb1 /mnt/x-data captive-ntfs defaults,noauto 0 0
```

As you can see I like to have a few extra powers on my filesystems. I have some CDs from ages ago which are broken multisessions and i'm hoping cdfs will fix them. It doesn't work either mind. I'm not going to be mounting all those NTFSs just yet of course. I need to be sue that the driver doesn't break my filesystems first, but hopefully we'll be in a world of goodfilesystemsharingness cross-OS

Anyone wanna paste a little "read this" link?  :smile:

---

### Post by shof2k on 2005-06-21
Well you could try 
[http://www.jankratochvil.net/project/captive/](http://www.jankratochvil.net/project/captive/)

to make sure you got captiventfs set up correctly :)

---

### Post by Dave_is_sexy on 2005-06-21
Man, I live on these forums. What does this mean?
```

# captive-cmdline \ --load-module=/var/lib/captive/ntoskrnl.exe \ --filesystem=/var/lib/captive/ntfs.sys \ --sandbox-server=/usr/sbin/captive-sandbox-server \ --bug-pathname=/tmp/captive-bug-%FT%T.captivebug.xml.gz \ --disk --rw /dev/hda1 # Now you can use ftp(1)-like command-line interface for the NTFS disk access.

```

I need to run it

---

### Post by Dave_is_sexy on 2005-06-21
Mmmmmmmmmmmmmmm

```

dave@D5:~$ captive-cmdline

Captive-ERROR **: File/device disk image pathname command-line argument requiredaborting...
Aborted
dave@D5:~$ aptive-cmdline \ --load-module=/var/lib/captive/ntoskrnl.exe \ --filesystem=/var/lib/captive/ntfs.sys \ --sandbox-server=/usr/sbin/captive-sandbox-server \ --bug-pathname=/tmp/captive-bug-%FT%T.captivebug.xml.gz \ --disk --rw /dev/hda1
bash: aptive-cmdline: command not found
dave@D5:~$ captive-cmdline --load-module=/var/lib/captive/ntoskrnl.exe --filesystem=/var/lib/captive/ntfs.sys --sandbox-server=/usr/sbin/captive-sandbox-server --bug-pathname=/tmp/captive-bug-%FT%T.captivebug.xml.gz --disk --rw /dev/hda1

Captive-ERROR **: image_iochannel open failed
aborting...
Aborted
dave@D5:~$
```

---

### Post by shof2k on 2005-06-21
Erm, forgive me if you already knew this but captive-ntfs works by 'borrowing' the microsoft ntfs driver modules ntoskrnl.exe and ntfs.sys.  I think it expects them to be in /var/lib/captive by default or you can hardcode an alternate location using the --load-module and --filesystem flags.  Do you have the modules available?

The link I gave previously showed what to do.  Good luck

---

### Post by Dave_is_sexy on 2005-06-21
yeah they're in there. infact for somereason so is cdfs.sys.

---

