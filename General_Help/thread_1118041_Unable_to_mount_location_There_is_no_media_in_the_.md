---
title: "Unable to mount location: There is no media in the drive."
date: 2009-04-06
forum: General Help
---

### Post by &lt;iostream&gt; on 2009-04-06
Hi!


I have recently installed ubuntu on my old Toshiba A105-S4384 laptop without much trouble. The only thing is, I have just upgraded from 8.04 to 8.10 and now I am unable to read/write from dvds or cds.

When I type "sudo mount /dev/scd0 -t iso9660 /mnt/cdrom" into the terminal, I get this: "mount: No medium found"

And when I type  ls "-l /dev/scd0" into the terminal, I get this: 
"brw-rw----+ 1 root cdrom 11, 0 2009-03-26 20:00 /dev/scd0"

And this is what I get from my fstab file:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=e9d80ddd-01ef-4b52-9768-98117d449019 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=70f8bcbb-bd4a-4347-8f2a-777bed200c83 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0



As far as I can tell, this is not hardware failure. I have been using this dvd drive for years and it has worked fine on xp/vista/windows 7/ and until recently ubuntu 8.04. 

Please help if there are any solutions. I would really like to have my drive working again so that I can restore some old files on my computer. Its kind of important...

--btw, I have a Lexmark X7170 all-in-one printer. Does anyone know where I can find drivers for it? I was able to find the sample sane driver for the scanner, but not the printer and from what I have herd, there isnt much I can do with Lexmark printers. I am just making sure that this is the case.

---

### Post by taurus on 2009-04-06
What kind of media (disc) do you have in the CD/DVD drive?

---

### Post by &lt;iostream&gt; on 2009-04-06
I am trying to use a data dvd and a cd with pictures on it.

---

### Post by fermin on 2009-04-16
I have this same problem. I also have a Toshiba Satellite laptop, model A105-S4397, and my CD/DVD-ROM drive stopped reading/writing discs. It doesn't reconize any disc anymore (doesn't mount them). Although, when a disc is inserted it does start working and makes all the noise as if it where reading it. I also don't think this is a hardware problem although I don't discard it could be. I don't actually remember when it stopped working and why.

The output of df -h is:
```
fermin@fermin-laptop:/dev$ df -h
S.ficheros            Tamaño Usado  Disp Uso% Montado en
/dev/sda3             144G  114G   25G  83% /
tmpfs                 500M     0  500M   0% /lib/init/rw
varrun                500M  376K  500M   1% /var/run
varlock               500M     0  500M   0% /var/lock
udev                  500M  2.8M  498M   1% /dev
tmpfs                 500M  1.2M  499M   1% /dev/shm
lrm                   500M  2.0M  498M   1% /lib/modules/2.6.27-14-generic/volatile
fermin@fermin-laptop:/dev$ 

```My fstab file contents is:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=45683907-77dc-40f0-a06f-23b56f0c122a /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=1fe3af90-1b7b-4589-8a7b-8efbedad4406 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```The output of lshw -class storage says:
```
fermin@fermin-laptop:/dev$ sudo lshw -class storage
  *-storage               
       description: Mass storage controller
       product: 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
       vendor: Texas Instruments
       physical id: 6.2
       bus info: pci@0000:07:06.2
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: storage pm bus_master cap_list
       configuration: driver=tifm_7xx1 latency=128 maxlatency=4 mingnt=7 module=tifm_7xx1
  *-ide
       description: IDE interface
       product: 82801GBM/GHM (ICH7 Family) SATA IDE Controller
       vendor: Intel Corporation
       physical id: 1f.2
       bus info: pci@0000:00:1f.2
       logical name: scsi0
       version: 02
       width: 32 bits
       clock: 66MHz
       capabilities: ide pm bus_master cap_list emulated
       configuration: driver=ata_piix latency=0 module=ata_piix

```I hope someone knows what could be wrong.

---

### Post by fermin on 2009-04-25
Bump.

---

### Post by &lt;iostream&gt; on 2009-05-23
I still haven't found a solution for this, but restarting the system occasionally solves this temporarily.

---

