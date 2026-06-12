---
title: "Permissions on a FAT32 partition are NOT ignored"
date: 2005-12-12
forum: General Help
---

### Post by cas_ on 2005-12-12
Hello!

I have a weird problem: file permissions set for files on my FAT32 partition are not forgotten after I unmount that partition. In my /etc/fstab I have a following entry:

/dev/hdc2       /media/dysk_wspolny vfat    quiet,user,noauto,dmask=0002,fmask=0113,gid=100,codepage=852,iocharset=utf8

I can mount and unmount /dev/hdc2 with no problem and permissions are being properly set to reflect fmask and dmask settings -- for most files. The bad thing happens if I create a new file (for example copy it from a CD). Nobody is given write permission for such a file and, what is the most surprising, these permissions are somehow preserved! They DON'T get reset after I unmount the partition. What is happening? How to turn this "feature" off?

---

### Post by blair on 2005-12-12
I don's know the exact answer to your question without researching the meaning of all the parameters you have there. I will say, that config string looks nothing like what is contained in the Ubuntu Starter Guide:

[http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows)

Suggest trying a different config string and see if that helps.

---

### Post by bb002 on 2005-12-12
Well your fstab line there is pretty whacky in my opinion. First off FAT in general (be it fat12, fat16, fat32) does not have unix style permissions support, period. However FAT has support for read only files(the only half-ass style of permissions fat has). Any and all directories/files on a cd/dvd are read-only. So when these files/folders are copied to a FAT partition their read-only permissions are preserved.


In your fstab string I don't know what "quiet,codepage=852,gid=100" are for.
I understand what the rest are for but I don't know what use dmask and fmask have on a permissionless Filesystem.

---

### Post by soulestream on 2005-12-13
first off dont ever put "quiet" in an fstab. If you have an error mounting it doesnt tell you, nor does it tell you if you have an error changing permissions. 

> understand what the rest are for but I don't know what use dmask and fmask have on a permissionless Filesystem.

you mean all those years of setting "read-only" did no good. :p 

fmask and dmask are interpretted by the OS to to the filesystem. So yes it does change permissions on fat32. 

soule

---

### Post by RAOF on 2005-12-13
[QUOTE=soulestream]...you mean all those years of setting "read-only" did no good. :p 
...[/QUOTE]
Well, they did **some** good.  They meant that windows would ask before deleting the file.  If you did it from the GUI.  Obviously, if you deleted it from the command line, it would cheerfully ignore the read-only bit.

---

### Post by soulestream on 2005-12-13
[cough]sarcasm[/cough]


soule

---

### Post by cas_ on 2005-12-13
[QUOTE=soulestream]first off dont ever put "quiet" in an fstab. If you have an error mounting it doesnt tell you, nor does it tell you if you have an error changing permissions.
[/QUOTE]
That's exactly what I want: no errors should be reported when system can't set access permissions for files on a FAT partition.

---

### Post by soulestream on 2005-12-13
so you are trying to figure out why you are having problems mounting and setting permission, but you have the thing that tells you why turned off. have fun.

>  Turn on the quiet flag.  Attempts to chown or chmod files do not
              return errors, although they fail. Use with caution!


from man mount

btw this is my fstab I have no problems reading and writing anything in it. You can adjust umask as needed.

/dev/sda2      /media/shared   vfat   rw,auto,umask=000   0    0



soule

---

### Post by cas_ on 2005-12-13
[QUOTE=soulestream]
from man mount
[/QUOTE]
I'm afraid you just don't understand what the problem is or maybe just what 'quiet' option really gives.

[QUOTE=soulestream]
You can adjust umask as needed.
[/QUOTE]
Perhaps you've missed something: I already have fmask and dmask set perfectly correct.

---

### Post by cas_ on 2005-12-13
[QUOTE=bb002]However FAT has support for read only files(the only half-ass style of permissions fat has).
[/QUOTE]
A good guess! I forgot about this feature. The question is: is there any way I can convince my Ubuntu not to touch the read-only setting on a FAT partition?

[QUOTE=bb002]
I understand what the rest are for but I don't know what use dmask and fmask have on a permissionless Filesystem.
[/QUOTE]
Huh? And what meaning would they have on a permission aware filesystem? According to man mount they can be applied ONLY to fat filesystems.

---

### Post by soulestream on 2005-12-13
if i understand correctly you have a rw setup on your fat32 partition. When you copy a cdrom (which is readonly) over to your filesystem, it stays readonly. You want it to become rw. Is that correct. If that is the case I have bo problems doing it.


soule


oh and what exactly does the "quiet" option do?

edit: you also have r-x set for 'other' on the directroy, make sure you are in gid 100.

---

