---
title: "Lost permission to alter Ipod"
date: 2009-03-18
forum: General Help
---

### Post by Melodic on 2009-03-18
Okey I'll try to include as much information as possible. 

I am running Intrepid
My Ipod is a 2nd generation shuffle 
gtkpod recognized it before as version: xB229
gtkpod is version 0.99.12

I had my Ipod working just perfectly before, and was using gtkpod with no problems. Recently I did introduce an external hard drive into my system. and played around a little bit with fdisk, mkfs, and fstab. That had been most of my recent usage of the shell commands.

yesterday I noticed my Ipod was not longer automounting. So I tried to mount it manually. The mountpoint could not be found so I 

$mkdir /media/ipod
and 
&mount /dev/sdc /media/ipod

but gtkpod was telling me I had lost permission to write to the disk

so I went through a series of attempts to correct it

I used chown and chmod on /media/ipod, and /dev/sdc 

I was getting an odd response from fdisk -l and did'nt know if trying to reformat would help so I followed the instructions someone had left on this forum to reformat, 
I repartitions with fdisk, but got an error when using Mkfs (something about not making a filesystem on a full disk)

so the last thing I tried was plugging it into my husbands microsoft box and letting itunes return it to factory settings, but still am not able to use gtkpod. 

The error I am getting is
"Opening of '/media/ipod/iPod_Control/iTunes/iTunesDB' for writing failed (Permission denied)."

a look at the proporties of Ipod_Control say's it is owned by root, with no writing capabilities for anyone else but when I try to "sudo chown" I get "chown: changing ownership of `/media/ipod/iPod_Control': Operation not permitted"

((oh and one more thing somehow between when I first noticed my problem, and when I started frantically throwing commands around to fix it the device name changed from sdc to sdd))

here is my fdisk -l and fstab if they help at all


Fdisk has a really odd entry but, I don't know maybe this is normal for an iPod shuffle
|||||||||||||||||||||||||||||||||||||||||||||||||||||||||
Disk /dev/sdd: 1015 MB, 1015021568 bytes
32 heads, 61 sectors/track, 253 cylinders
Units = cylinders of 1952 * 2048 = 3997696 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   ?      398636      983425  2283019262   72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(398635, 6, 23)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(983424, 30, 61)
Partition 1 does not end on cylinder boundary.
/dev/sdd2   ?       86419     1078237  3872056480   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(86418, 26, 1)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(1078236, 17, 53)
Partition 2 does not end on cylinder boundary.
/dev/sdd3   ?      957932     1949749  3872056384   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(957931, 2, 32)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(1949748, 25, 36)
Partition 3 does not end on cylinder boundary.
/dev/sdd4   ?     1478321     1478349      110998    d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(1478320, 8, 25)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(1478348, 22, 13)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order
||||||||||||||||||||||||||||||||||||||||||||||||||


Fstab still reflects a dev named sdc, but maybe there is something in there that was keeping it from automounting

also does anyone know why the system would have assigned it a new name? there is now no sdc recognized by my system

||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||
proc            /proc           proc    defaults        0       0
UUID=0872af16-664f-45f6-bb17-501384776d68 /               ext3    relatime,errors=remount-ro 0       1
UUID=967d8be5-d420-4291-8e22-9a84dc200e92 /home           ext3    relatime        0       2
UUID=eebcc0ff-fb50-4e88-8003-27a956cd4f35 /usr            ext3    relatime        0       2
UUID=935150c7-767e-48ad-a617-e727128e9987 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
    *

/dev/sdb1    /media/terraspace   ext3    defaults     0        2

/dev/sdc     /media/ipod         vfat    defaults     0        2
||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||||


I know thats a lot of information, and I am sure most of it is useless, but if you can make any sense of it at all please let me know what I am missing. I am kinda new to this linux thing (like 2 months) and up till now have been able to fake my way through most problems. This seems to have eluded me though


thnxx
    -Melodic

---

### Post by circa82 on 2009-03-18
If you still have the /ipod folder under /media, you should remove it. Also remove the ipod entry in /etc/fstab '[color=red]/dev/sdc /media/ipod vfat defaults 0 2[/color]' as neither are required.

Device names can and often will change, especially when more than one external is being used. It's better to use UUID's or LABEL's, but best to avoid /etc/fstab altogether. Automounting is exactly what the hal daemon (hald) is for. It handles removable media (CD/DVD's & USB devices) and uses dynamic mount points. Permissions are set through policies, but you may not need that.

After you've removed both the folder and fstab entry, plug in your ipod and verify that it's being mounted for you. You should have an icon on your desktop and the mount point should be under /media. 

Note: The same should be true for your external HDD, unless it's NTFS, then you'll need to create a new policy for user access.

---

### Post by Melodic on 2009-03-18
unfortunately that didn't do it

first I sudo umount /media/ipod

i successfully removed the file from /media

$melodic@diapason:/media$ ls
$cdrom  cdrom0  terraspace
$melodic@diapason:/media$ 

and removed the line from fstab

proc            /proc           proc    defaults        0       0
UUID=0872af16-664f-45f6-bb17-501384776d68 /               ext3    relatime,errors=remount-ro 0       1
UUID=967d8be5-d420-4291-8e22-9a84dc200e92 /home           ext3    relatime        0       2
UUID=eebcc0ff-fb50-4e88-8003-27a956cd4f35 /usr            ext3    relatime        0       2
UUID=935150c7-767e-48ad-a617-e727128e9987 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
    *

/dev/sdb1    /media/terraspace   ext3    defaults     0        

I physically removed the ipod from dock, and reset it

nothing happens

---

### Post by circa82 on 2009-03-18
I would unplug the ipod, reboot, and try again.

Also, would you happen to have a link to for the formatting guide you used?

---

### Post by Melodic on 2009-03-18
[http://people.csail.mit.edu/adonovan/hacks/ipod.html](http://people.csail.mit.edu/adonovan/hacks/ipod.html)

I followed these instructions
I did not format with 2 partitions though, as I read elsewhere the shuffle operates with only one partition. 

but none of that should apply now, as I had Itunes return the ipod to factory settings

---

### Post by Melodic on 2009-03-18
hmm, the reboot didn't do it either.

---

### Post by circa82 on 2009-03-18
If you would do two things...

1st, open a terminal and run the following:
```
# [color=blue]sudo /etc/rc.d/hal start[/color]
```
If the response is hal is already running, good news.

2nd, with the ipod unplugged and the terminal open run the following:
```
# [color=blue]tail -f /var/log/syslog[/color]
```
Then insert the ipod. If errors occur, please post.

hal requires that your user be included in specific groups; though Ubuntu (being user friendly) should do it for you, so unless you're using a new user, this wouldn't be the problem.

Also, as far as the partitioning goes, your fdisk output suggest multiple partitions on the ipod; not just one.

---

### Post by Melodic on 2009-03-18
sudo: /etc/rc.d/hal: command not found


melodic@diapason:~$ tail -f /var/log/syslog
Mar 18 18:15:01 diapason kernel: [  264.220446]  sdc: sdc1 sdc2
Mar 18 18:15:01 diapason kernel: [  264.230668] sd 3:0:0:0: [sdc] Attached SCSI disk
Mar 18 18:15:01 diapason kernel: [  264.231164] sd 3:0:0:0: Attached scsi generic sg3 type 0
Mar 18 18:17:01 diapason /USR/SBIN/CRON[7192]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Mar 18 18:17:08 diapason kernel: [  391.430362] kjournald starting.  Commit interval 5 seconds
Mar 18 18:17:08 diapason kernel: [  391.432181] EXT3 FS on sdc1, internal journal
Mar 18 18:17:08 diapason kernel: [  391.432456] EXT3-fs: mounted filesystem with ordered data mode.
Mar 18 18:20:02 diapason /USR/SBIN/CRON[7365]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Mar 18 18:30:03 diapason /USR/SBIN/CRON[7767]: (root) CMD ([ -x /usr/sbin/update-motd ] && /usr/sbin/update-motd 2>/dev/null)
Mar 18 18:34:14 diapason kernel: [ 1417.087841] usb 5-5: USB disconnect, address 2

---

### Post by circa82 on 2009-03-18
From a terminal, if you would run the following and post the output (if any):
```
# [color=blue]ps -A | grep hal[/color]
```

---

### Post by Melodic on 2009-03-18
melodic@diapason:~$ ps -A | grep hal
 5994 ?        00:00:03 hald
 5995 ?        00:00:00 hald-runner
 6014 ?        00:00:00 hald-addon-dell
 6023 ?        00:00:00 hald-addon-cpuf
 6024 ?        00:00:00 hald-addon-acpi
 6025 ?        00:00:00 hald-addon-inpu
 6057 ?        00:00:01 hald-addon-stor
 6688 ?        00:00:00 gvfs-hal-volume
 8178 ?        00:00:00 hald-addon-stor
melodic@diapason:~$

---

### Post by circa82 on 2009-03-18
Thank you. So hal is running. 

Now, if you (with the ipod unplugged) run the following command:
```
# [color=blue]lshal -m[/color]  <-- that's LshaL in lowercase letters
```
You should be greeted with:
[color=red]Start monitoring devicelist:[/color]
If you would then connect your ipod and post the output given (if any). 

Also, before the trouble started, what mount point was the ipod using (which folder) and had you created that folder prior to or was it created for you?

---

### Post by Melodic on 2009-03-18
Start monitoring devicelist:
-------------------------------------------------
19:38:25.208: usb_device_5ac_1301_000A27001C71CC6F added
19:38:25.368: usb_device_5ac_1301_000A27001C71CC6F_if0 added
19:38:25.833: usb_device_5ac_1301_000A27001C71CC6F_if0_scsi_host added
19:38:30.054: usb_device_5ac_1301_000A27001C71CC6F_if0_scsi_host_0 added
19:38:30.065: usb_device_5ac_1301_000A27001C71CC6F_if0_scsi_host_0_scsi_device_lun0 added
19:38:30.222: usb_device_5ac_1301_000A27001C71CC6F_if0_scsi_host_0_scsi_device_lun0_scsi_generic added
19:38:38.373: storage_serial_Apple_iPod_000A27001C71CC6F_0_0 added
19:38:38.421: storage_serial_Apple_iPod_000A27001C71CC6F_0_0 property info.interfaces = {'org.freedesktop.Hal.Device.Storage', 'org.freedesktop.Hal.Device.Storage', 'org.freedesktop.Hal.Device.Storage.Removable'}
19:38:39.029: volume_uuid_508F_F863 added


before it was auto mounting at /media/ipod

---

### Post by Melodic on 2009-03-24
no one else has any advice?

---

