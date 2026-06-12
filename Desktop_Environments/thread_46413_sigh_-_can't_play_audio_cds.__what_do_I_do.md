---
title: "sigh - can't play audio cds.  what do I do???"
date: 2005-07-04
forum: Desktop Environments
---

### Post by linuxted on 2005-07-04
When I put a store-bought CD in my cdrom and try to play it, it doesn't work.

With CDplayer I get a "Drive Error".  When I try to change the preferences I get 
You do not seem to have permission to access /dev/hdd.
This means that the CD player will not be able to run.


When I try to use SoundJuicer I get:
Sound Juicer could not access the CD-ROM device '/dev/hdd'
Reason: Permission denied

When I try to use Totem I get:

Failed to open device /dev/hdc for reading: Permission denied

Looking at /etc/fstab I have the following:# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/sda1       /mnt/external   ext3    noauto,users    0       0
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdd        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0



Can anyone help?  This is very frustrating for this new Ubuntu user.


Thank you

---

### Post by brim4brim on 2005-07-04
Is it a Sony CD.  They have just developed a new form of protection for CD's, maybe it's not compatible with Linux yet.

---

### Post by chalker on 2005-07-04
Since everything is complaining about permissions then try changing the permissions by typing: sudo chmod 777 /dev/hdd or hdc, whatevery your cdrom happens to be.  777 is the permission code that will allow everyone to read, write and execute that file.  Since the file is a link to your cdrom it is okay, but don't change important file to that permission code for system files.

---

### Post by GMachine_24 on 2005-07-04
Perhaps turn off the sound server (uncheck the boxes under configuration) .... before I did this I was not able to play mp3 or wav files or install RealPlayer......

---

### Post by jeremy on 2005-07-05
Do you have the analogue cable attached to the cd player?

---

