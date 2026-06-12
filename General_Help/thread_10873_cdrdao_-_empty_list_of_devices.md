---
title: "cdrdao - empty list of devices"
date: 2005-01-12
forum: General Help
---

### Post by svik on 2005-01-12
Hello,

I have a problem with cdrdao. When I execute **cdrdao scanbus** I got an emty list of devices. I also try to find something about it in the inet but without success. 
Execution of **cdrdao write videocd.cue** returns me an error:
Can't open /dev/cdrecorder

Any ideas?

Thanks in advance.
Svik

---

### Post by barbarian on 2005-01-12
try *sudo cdrdao scanbus*, or *sudo cdrdao scanbus /dev/hdc*

---

### Post by svik on 2005-01-12
I have already tried this no success.
Now I can burn the disk with command **cdrdao write --device /dev/hdc videocd.cue**. But I wondering why a standard way is not working.

That is a result of the command **cdrdao write videocd.cue**: 
[I]Cdrdao version 1.1.9 - (C) Andreas Mueller <andreas@daneb.de>
  SCSI interface library - (C) Joerg Schilling
  Paranoia DAE library - (C) Monty

Check [http://cdrdao.sourceforge.net/drives.html#dt](http://cdrdao.sourceforge.net/drives.html#dt) for current driver tables.

ERROR: Cannot open SCSI device '/dev/cdrecorder': Cannot open '/dev/cdrecorder'
Supported SCSI transports for this platform:

Transport name:         sg
Transport descr.:       Generic transport independent SCSI
Transp. layer ind.:
Target specifier:       bus,target,lun
Target example:         1,2,0
SCSI Bus scanning:      supported
Open via UNIX device:   not supported

Transport name:         pg
Transport descr.:       SCSI transport for ATAPI over Parallel Port
Transp. layer ind.:
Target specifier:       bus,target,lun
Target example:         1,2,0
SCSI Bus scanning:      supported
Open via UNIX device:   not supported

Transport name:         ATA
Transport descr.:       ATA Packet specific SCSI transport
Transp. layer ind.:     ATAPI:
Target specifier:       bus,target,lun
Target example:         ATAPI:1,2,0
SCSI Bus scanning:      supported
Open via UNIX device:   not supported

Transport name:         ATA
Transport descr.:       ATA Packet specific SCSI transport using sg interface
Transp. layer ind.:     ATA:
Target specifier:       bus,target,lun
Target example:         1,2,0
SCSI Bus scanning:      supported
Open via UNIX device:   not supported
ERROR: Please use option '--device [proto:]bus,id,lun', e.g. --device 0,6,0 or --device ATAPI:0,0,0
ERROR: Cannot setup device /dev/cdrecorder.[/I]

---

### Post by barbarian on 2005-01-13
If you have 2.6.x kernel then you don't need scsi emulation.
If you have 2.4.x - try *lsmod | grep scsi*

---

### Post by svik on 2005-01-13
I have 2.6... kernel. 
So, you think that it is normal to burn in that way: **cdrdao write --device /dev/hdc videocd.cue**?

---

### Post by barbarian on 2005-01-13
IMHO if it works, why not.. 


I'm in ubuntu very recently, so I'm burning CD-R with:
cdrecord -v speed=2 dev=/dev/hdc -audio my_cool_track.cdr my_cool_track2.cdr..
Maybe it's not elegant way, but it works.



Btw.,  my for me:

sudo cdrdao scanbus /dev/hdc
Password:
Cdrdao version 1.1.9 - (C) Andreas Mueller <andreas@daneb.de>
  SCSI interface library - (C) Joerg Schilling
  Paranoia DAE library - (C) Monty

Check [http://cdrdao.sourceforge.net/drives.html#dt](http://cdrdao.sourceforge.net/drives.html#dt) for current driver tables.

Using libscg version 'schily-0.8'

ATA:1,0,0            LITE-ON , COMBO LTC-48161H, KH0P

---

