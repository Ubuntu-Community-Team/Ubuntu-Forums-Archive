---
title: "turning on DMA"
date: 2005-11-05
forum: Desktop Environments
---

### Post by coldrick on 2005-11-05
If I do 'sudo hdparm /dev/cdrom', I get:

/dev/cdrom:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

So I'm sorta hesitant about turning DMA on via hdparm.

Any idea why this error message appears? 

Regards,
David

---

### Post by 23meg on 2005-11-05
Is your cdrom connected via SATA or IDE? If it's SATA hdparm won't let you tweak its settings (you probably won't need to anyway). There's also a chance that your drive isn't supported for this operation by hdparm or the kernel; in that case you may need to rebuild a kernel with proper support for your drive but I can't be of help there since I've never done it myself.

---

### Post by coldrick on 2005-11-06
How do I tell whether it's SATA or IDE?

Regards,
David

---

### Post by jvictor on 2005-11-06
Open u p the machine and see if the connecter cable is a **thin** one or **flat BIG** one.. if its thin its sata if not its PATA

---

### Post by jvictor on 2005-11-06
Also use

hdparm -d1 /dev/cdrom

let us know if it works fine

---

### Post by coldrick on 2005-11-14
Sorry - got involved in other things.

This is a Dell Inspiron 9300 laptop: the CD/DVD drive is a "Sony DW-D56A slim 8x DVD+/-RW" with an ATAPI interface, if that helps.

If I do sudo hdparm -d1 /dev/cdrom, I get

/dev/cdrom:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device

Regards,
David

---

### Post by poptones on 2005-11-14
/dev/cdrom isn't a proper device for that. Try /dev/hdb or /dev/hdc and it should work.

---

### Post by deepclutch on 2005-11-14
great thanks guys.for me DMA on worked.will i need to do "hdparm -d1 /dev/cdrom" every boot? OR should i enter this values to any config file(s)?

---

### Post by spade_shark on 2005-11-14
Try this: "hdparm -k1 -d1 /dev/cdrom"  The (k) flag saves the settings.  You may also look into the -c1 option.  This flag (c) will enable 32-bit mode.  Be careful with this (c) flag.  If your device (hard drive, cdrom, dvdrom, etc )supports 32bit, then your hdparm may try:

"hdparm -k1 -c1 -d1 /dev/hda"

with results:

/dev/hda:
 setting 32-bit IO_support flag to 1
 setting using_dma to 1 (on)
 setting keep_settings to 1 (on)
 IO_support   =  1 (32-bit)
 using_dma    =  1 (on)
 keepsettings =  1 (on)

---

### Post by spade_shark on 2005-11-15
Some other things to try:  (replace hda with device letter)

"hdparm -iv /dev/hda"  or maybe "hdparm -tT /dev/hda"

Once you are happy with results save to /etc/hdparm.conf file.  Here is a sample from mine.  (The command line statements are loaded later in startup, so try to stay with newer naming convention)

"# hda-40GB Fijitsu
/dev/hda {
        io32_support = 1
        dma = on
        interrupt_unmask = on
        write_cache = off
}

# hde-82GB Maxtor
/dev/hde {
        io32_support = 1
        dma = on
        interrupt_unmask = on
        write_cache = off
}

# hdg-82GB Maxtor
/dev/hdg {
        io32_support = 1
        dma = on
        interrupt_unmask = on
        write_cache = off
}"

note: write_cache should be disabled with journaling file systems.

---

### Post by coldrick on 2005-11-15
I have no "hd" devices in /dev, my hard drives are sda*
My fstab looks like:
/dev/sda6       /               reiserfs notail          0       1
/dev/sda2	/media/sda2	ntfs	ro,auto,umask=000 0 0
/dev/sda5       /media/sda5     vfat    rw,auto,umask=000 0 0
/dev/sda7       none            swap    sw              0       0

If I try the command with sdb, sdc, hda, hdb, hdc,  all I get is "No such device"

Is there some way I can tell what the dev is for the CD/DVD drive? Certainly doesn't seem to be possible with nautilus and "properties".

Regards,
David

---

### Post by Pablo_Escobar on 2005-11-15
Your fstab tells that only HDD (SATA) partitions are mounted, no CD drive. Are You sure that's Your whole fstab file ?
Are You able to access a CD from Ubuntu when You pop it into the drive ?

---

### Post by coldrick on 2005-11-15
Yes, that's all of it, save the comments at the top.

And yes, I can access CDs or DVDs when they're mounted.

For example, the attached screenshot shows nautilus exploring the Breezy CD.

Regards,
David

---

### Post by Pablo_Escobar on 2005-11-15
You mount CD's via CLI every time You pop them in or they mount themselves ?

---

### Post by Miguel on 2005-11-15
He is probably using Gnome's automounter feature.

I also don't have any CD-ROM or USB memory stick lines in fstab, and they work OK under Gnome. However, I must write the whole command (sudo mount -t filesystem device mountpoint) in CLI when I'm in Xfce.

---

### Post by coldrick on 2005-11-15
yes, they automount (if I had to cli-mount them, I'd know what the device was, yes?) :) 

Regards,
David

---

### Post by Pablo_Escobar on 2005-11-15
I'll try to post something later on, when I'm back from work, and I'll be on my U box.

---

### Post by Miguel on 2005-11-15
Coldrick,

I have an idea. Mabye we can guess where is your CD-ROM. Could you put a data CD on your laptop and, after it's mounted, type "df -h" in a terminal? 

I'm on debian sarge right now (my ubuntu laptop has an expiring HD), so I usually mount my CD manually, but I get the following:
```

miguel@lcpy44:~$ df -h
S.ficheros          Tamaño Usado  Disp Uso% Montado en
/dev/hda3             6,1G  3,8G  2,4G  62% /
tmpfs                 245M     0  245M   0% /dev/shm
/dev/hda4              19G   12G  7,0G  63% /home
tmpfs                  10M  748K  9,3M   8% /dev
/dev/hdc              265M  265M     0 100% /media/cdrom0

```

Here, you can see my cdrom is /dev/hdc. As a sidenote, I can also mount it from /dev/cdrom... but df -h still shows that it was mounted from /dev/hdc. 

I would guess your CD will be either /dev/cdrom or /dev/sdc.

Hope it helps,

Miguel

---

### Post by coldrick on 2005-11-15
Hi Miguel,

I get:
/dev/scd0             618M  618M     0 100% /media/cdrecorder,

so I guess it's scd.

However, sudo hdparm -d1 /dev/scd gives no such device, and the same for scd0 gives the now-familiar:
/dev/scd0:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device

Regards,
David

---

### Post by jclemon on 2005-11-18
i get the same message when trying to enable DMA on my drive (LITE-ON DVDRW SOHW-1673S)

jclemon@bosco:~$ sudo hdparm -d1 /dev/cdrom
/dev/cdrom:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
jclemon@bosco:~$ sudo hdparm /dev/cdrom
/dev/cdrom:
 IO_support   =  0 (default 16-bit)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Inappropriate ioctl for device

i have yet to find any clear solutions. i can burn CDs by right-clicking an ISO and burn directly from gnome, but if i try in gnomebaker or k3b i get errors and can't burn at all. HELP!

---

### Post by dcstar on 2005-11-19
Be warned, when I enabled DMA (in my /etc/hdparm.conf file) for my DVD/RW drive it stopped detecting audio CDs.

As soon as I turned it back off, everything worked again (and it still burned media ok either way).

---

### Post by Pretzal on 2005-11-19
I too have the same problem in that I cant turn on DMA. When I do a df -h i get: 
glasson@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3             7.4G  2.6G  4.4G  38% /
tmpfs                 126M     0  126M   0% /dev/shm
tmpfs                 126M   13M  113M  10% /lib/modules/2.6.12-9-386/volatile
/dev/hda1              22G  4.9G   17G  23% /media/windows
/dev/hda5             2.2G   46M  2.2G   3% /media/Shared
/dev/hdc              197M  197M     0 100% /media/cdrom0

and doing the hdparm /dev/hdd command gives me:
glasson@ubuntu:~$ hdparm /dev/hdd

/dev/hdd:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument

Has anyone got any ideas? I have tried automatix which wasnt able to help.

Thanks

---

### Post by RAOF on 2005-11-19
[QUOTE=Pretzal]...
/dev/hdc              197M  197M     0 100% /media/cdrom0

and doing the hdparm /dev/hdd command gives me:
glasson@ubuntu:~$ hdparm /dev/hdd
...[/QUOTE]
That should actually have been /dev/hd**c**.  If you run hdparm /dev/hdc it should not give you that error (which, if my memory serves, means "Can't get the disc geometry - essentially "how big" it is.  From the output of your commands, I'd guess that you have 2 cd drives, one with a disc in (/dev/hdc), one without (/dev/hdd) - and you can't get the "size" of a cd drive with no disc in it :))

Incidentally, the reason that DMA is not on by default is that there are too many drive/controller combinations which don't work properly with DMA enabled.  So, if your drive doesn't work once you've enabled DMA, you've got a good suspect :)

---

### Post by Pretzal on 2005-11-20
You are spot on RAOF I do have 2 CD drives. When I do hdparm /dev/hdc i Get:

/dev/hdc:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 HDIO_GETGEO failed: Invalid argument
glasson@ubuntu:~$

Why then do I still get errors for all the burning programs I try and run like DVD:RIP which says:
cdrecord device (n,n,n or no filename): n,n,n has not format n,n,n and is no file: NOT OK??

---

### Post by jpkotta on 2005-12-18
I have a DVD drive using libata too (shows up as /dev/scd0), and I had a hellish time getting DMA.  What finally worked for me was to remove the ide_generic module.  See this [post]("http://ubuntuforums.org/showpost.php?p=584397&postcount=13") for more.

---

