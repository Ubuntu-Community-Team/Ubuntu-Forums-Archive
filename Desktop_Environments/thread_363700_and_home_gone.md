---
title: "/ and /home gone"
date: 2007-02-17
forum: Desktop Environments
---

### Post by jpgeerets on 2007-02-17
hi folks,

my laptop works grat for 2 weeks with kubuntu...

nog i shutdown and move it 200km.....

when i will boot it, it goes wrong.
i cant launch kde anymore.

when i boot in safe mode and give the command df -k, i cant see / and /home anymore.
it seems they r not mount anymore...

also when i go into /home, this is empty.

that's also why kde want boot anymore.

anyone any idea?

i hope i can get this thing back to work.....

tia!!

Jean-Paul

---

### Post by taurus on 2007-02-17
What does your /etc/fstab look like?

```
cat /etc/fstab
```

---

### Post by jpgeerets on 2007-02-17
tnx for your fast reply....

at this moment im happy i have windows...

my fstab:

---
;/dev/sda1 /var/run/drives/300-1gb ntfs defaults 0 0
;/dev/sda2 /var/run/drives/300gb-2 ext3 defaults 0 0
;/dev/sda1 /var/run/drives/300-1gb ntfs defaults 0 0
;/dev/sda2 /var/run/drives/300gb-2 ext3 defaults 0 0
;/dev/sda1 /var/run/drives/300-1gb ntfs defaults 0 0
;/dev/sda2 /var/run/drives/300gb-2 ext3 defaults 0 0
/dev/sda1 /var/run/drives/300-1gb ntfs defaults 0 0
/dev/sda2 /var/run/drives/300gb-2 ext3 defaults 0 0
/dev/sda1 /var/run/drives/300-1gb ntfs defaults 0 0
/dev/sda2 /var/run/drives/300gb-2 ext3 defaults 0 0
---

this only is my ext. usb drive... no internal drv.

Jean-Paul

---

### Post by taurus on 2007-02-17
Is that really your /etc/fstab?  That is the weirdest /etc/fstab that I have ever seen before.

So you installed Kubuntu on an external harddrive with your laptop!

---

### Post by jpgeerets on 2007-02-17
no no.

i installed it on my harddisk.
my local harddisk.

my external drive i use for transport stuff.

how does your fstab look like?
perhaps i just can replace mine with your example...

i work with kubuntu for more then a year on my laptop...
never had this strange problem.

---

### Post by taurus on 2007-02-17
Boot into recovery mode from GRUB menu and at the prompt, paste the output of your /etc/fstab here again.

```
cat /etc/fstab
```

---

### Post by mcduck on 2007-02-17
There sure is lots of strange things in your fstab :o

Mine looks like this:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=365d417b-a50b-4df9-8249-f17f37a542aa /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
 UUID=9877-489A  /media/hda1     vfat    noauto,defaults,utf8,umask=007,gid=46 0       0
# /dev/hda2
 UUID=B043-DF50  /media/hda2     vfat    noauto,defaults,utf8,umask=007,gid=46 0       0
# /dev/hda6
UUID=66280a28-42cb-4664-ad19-0a0753ebda3a /mnt/storage    ext3    defaults        0       2
# /dev/hda5
UUID=5eb2a44a-b765-4cd2-abe9-751ff3aa0046 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
```
(note that you can't use the same UUID's, and also you need to make sure you use right devices & have the mount points..

---

### Post by jpgeerets on 2007-02-17
that's what i did....

see my post above....

i cant boot in normal may.

---

### Post by kvonb on 2007-02-17
Sounds to me like your hard disk is damaged, run fsck on it, or a third party disk checker tool!

---

### Post by jpgeerets on 2007-02-17
yeah, 
this looks familiar to me... :-)
i see you also have an update to the latest kubuntu... :-)
perhaps i can try this to mine kubuntu.....

Tnx!

---

### Post by jpgeerets on 2007-02-17
i can reach everything i want when i use windows with IFSdrives.
that way i can mount ext3 to windows... :-)
so diskdamge i dont think....

---

### Post by jpgeerets on 2007-02-17
ok folks,

i fount another file...
it's called fstab.pre-uuid

i gues this is a backup file of the system, before an update. perhaps before the kernel update....?
someone know this?
when i looks in it, it looks fine to me... :-)
perhaps i just have to try this one.. rename and cross fingers.... :-)

---

### Post by jpgeerets on 2007-02-17
ok.

what have i done....

my fstab was corrupt.
there was a file, called 
```
fstab.pre-uuid
```
i guess the system made this before doing a (kernel) update.
so, i also guess this update has crashed my fstab file.

i rename fstab to fstab-old
the i made a copy of fstab.pre-uuid to fstab
after that, i boot the system and all went well.

can this be happend after a automatic update?
this must be an update of the last 2 weeks.
the previous shutdown was 2 weeks a go...

i hope this will help people with the same problem.

tnx everyone!!!

---

### Post by PurplePenguin on 2007-02-17
Thanks for replying and saying that everything works.  It should definitely help the next guy to come along with the same problem! :)

---

