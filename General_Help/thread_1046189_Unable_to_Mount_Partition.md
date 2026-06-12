---
title: "Unable to Mount Partition"
date: 2009-01-21
forum: General Help
---

### Post by aircombat on 2009-01-21
I have recently installed UBuntu. Yesterday, I left my comp on in the night to finish a download and the power supply went out in the night. THE UPS did BEEP, but I was too lazy to get up and switch off the comp. Today morning onwards Windows is taking its revenge by giving me the BSOD. I logged into Ubuntu and tried mounting my 2 partitions which hav eall the data but am unable to do it. 

The error is as below.
> $LogFile indicates unclean shutdown (0,0)Failed to mount '/dev/sda5': Operation not supported Mount is denied because NTFS is marked to be in use. Choose one action: Choice 1: If you have Windows then disconnect the external devices by clicking on te 'Safely Remove Hardware' icon in the Windows taskbar then shutdown Windows cleanly. Choice 2: If you don't have Windows you can use the 'force' option for your own responsibility. For example type on the command line: mount -t ntfs-3g/dev/sda5/media/PROFFESSIONAL -o force Or add the option to the relevant row in the etc/fstab file: /dev/sda5/media/PROFFESSIONAL ntfs-3g force 00

I have already tried the Terminal option and got the following result

> 
arunava@arunava-desktop:~$ mount -t ntfs-3g/dev/sda5/media/PROFFESSIONAL -o force
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
arunava@arunava-desktop:~$ 
arunava@arunava-desktop:~$ 


I don't have the original Windows CD now. Its at my parents place. So I need to access my DATA from Ubuntu for the moment. Please help.

---

### Post by sisco311 on 2009-01-21
try:
```

sudo mkdir /media/PROFFESSIONAL
sudo mount -t ntfs-3g /dev/sda5 /media/PROFFESSIONAL -o force,defaults,umask=002,gid=46
```

---

### Post by aircombat on 2009-01-21
> arunava@arunava-desktop:~$ mkdir /media/PROFFESSIONAL
mkdir: cannot create directory `/media/PROFFESSIONAL': Permission denied


Any idea why that happened, and what is the solution?

---

### Post by taurus on 2009-01-21
Or

```
sudo apt-get update
sudo apt-get install ntfsprogs
sudo ntfsfix /dev/sda5
```

---

### Post by taurus on 2009-01-21
> **aircombat said:**
> Any idea why that happened, and what is the solution?

You need to include the sudo in front of the command.

```
sudo mkdir /media/PROFFESSIONAL
```

---

### Post by aircombat on 2009-01-21
> **taurus said:**
> You need to include the sudo in front of the command.

```
sudo mkdir /media/PROFFESSIONAL
```

YA silly me. However, status quo remains unchanged.

> 
arunava@arunava-desktop:~$ sudo mkdir /media/PROFFESSIONAL
arunava@arunava-desktop:~$ sudo mount -t ntfs-3g /dev/sda5/media/PROFFESSIONAL -o force,defaults,unmask==002,gid=46
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
arunava@arunava-desktop:~$ 



---

### Post by drs305 on 2009-01-21
> sudo mount -t ntfs-3g /dev/[COLOR="Red"]sda5/med[/COLOR]ia/PROFFESSIONAL -o force,defaults,[COLOR="Red"]unm[/COLOR]ask[COLOR="Red"]==[/COLOR]002,gid=46

You need a space separating the device and mount point and one less "=" sign, and fix the "umask" typo:
```

sudo mount -t ntfs-3g /dev/sda5 /media/PROFFESSIONAL -o force,defaults,umask=002,gid=46

```

Cut & Paste is a wonderful thing!   ;-)

---

### Post by aircombat on 2009-01-21
> **drs305 said:**
> You need a space separating the device and mount point and one less "=" sign, and fix the "umask" typo:
```

sudo mount -t ntfs-3g /dev/sda5 /media/PROFFESSIONAL -o force,defaults,umask=002,gid=46

```

Cut & Paste is a wonderful thing!   ;-)

Ya I did CUT-PASTE and it worked. So this THread can be closed. Thanx a lot all of u

---

