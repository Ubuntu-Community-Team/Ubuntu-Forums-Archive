---
title: "dd permission denied unless file system is FAT32"
date: 2009-05-08
forum: General Help
---

### Post by djrakun on 2009-05-08
Hi all,

Until today I was backing up my systems using tar.  I decided to give dd a whirl as it seems to be common advice for the best backup procedure.  I was able to make a 'test' backup on a new system pretty easy, but on my second attempt I ran into a problem...

I'm compressing the image by piping it to bzip and dropping the file onto a usb flash drive with this terminal command



dd if=/dev/sda | bzip2 -z > /media/disk-1/pc.img.bz2




If I attempt to do this on an ext-2 or ext-3 filesystem as superuser i get a response


bash: /media/disk-1/pc.img.bz2: Permission denied


however if i format sdb ( disk-1) to FAT32 the dd command works fine.  If I had to guess FAT32 works because of perms ( or lack of on FAT32 drives).  when I format the drive the owner is root and I would assume that 'sudo' would be enough to grant me permission, but apparently not.

does anyone know what permissions I need to set to copy my image over to an ext-3 formatted usb drive?  I don't want to be restricted to 4gb on my image file

Thanks a mil

---

### Post by Alterax on 2009-05-08
try going into a full-out root shell with **sudo -i** first.

If it does work, type **cat /etc/mtab | grep media** and post the result.
It may be merely an issue with permissions and how they are handled with sudo.

---

### Post by djrakun on 2009-05-11
you were right, Alterax.  sudo -i worked brilliantly.  you will have to explain when you get the chance.  I'm concerned that cron will not be able to do this task as I'm planning to schedule a weekly backup for my machines using this command.

this is the output from cat for that drive:

/dev/sdc1 /media/disk-1 ext3 rw,nosuid,nodev,uhelper=hal 0 0


Thanks for your quick and accurate reply :KS

---

