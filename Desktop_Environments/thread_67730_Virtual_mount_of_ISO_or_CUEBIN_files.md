---
title: "Virtual mount of ISO or CUE/BIN files ???"
date: 2005-09-21
forum: Desktop Environments
---

### Post by daller on 2005-09-21
Hi All,

How do I mount an ISO or CUE/BIN file?

A commandline-solution is O.K. - but what i'm searching for, is a GUI app!

thanks!

---

### Post by xmastree on 2005-09-21
There's a command line option in [the guide](http://www.ubuntuguide.org) but I can't connect to it right now, so I can't point you to the relevant section. Suggest you search for **ISO**.

Edit: Guide is down, use the mirror instead
[http://www.frankandjacq.com/ubuntuguide/5.04/index.html#mountunmountisofileswithoutburning](http://www.frankandjacq.com/ubuntuguide/5.04/index.html#mountunmountisofileswithoutburning)

---

### Post by daller on 2005-09-21
Great! - but what about cue/bin files?

...And a GUI would be really nice for both!

---

### Post by tambooki on 2005-09-21
I typically use bchunk to convert cue/bin files to iso. There may be a simple way to mount them (I'm fairly certain I've come across (cli) apps that do it), but I also prefer to have all my images as isos... don't know why ;). As for GUI apps; sorry, no help there.

---

### Post by mlomker on 2005-09-21
[QUOTE=daller]Great! - but what about cue/bin files?
[/QUOTE]

You want [cdemu](http://cdemu.org/).  It has to be compiled as a kernel module but it wasn't that tough to get going.  I'm not aware of any GUI's for this stuff, but there is [this.](http://www.kde-apps.org/content/show.php?content=11577)

---

### Post by daller on 2005-10-03
With the GUI i get this error:

ERROR: "system:/home/downloads/iso/Kompas/k3b_0.iso" is not readable, check file permissions!

I'm not asked for a root password - shouldn't I?

---

### Post by mlomker on 2005-10-03
> I'm not asked for a root password - shouldn't I?

No, the script wasn't designed for Ubuntu.  Where are you saving files such that your user account wouldn't have permissions?  I download .iso's into my /home/username directory and it inherits the proper permissions.

I just tested the script and it works when the permissions are right.  Do you know how to change permissions?

```

sudo chmod 777 *filename.iso*

```

That will give everyone full permissions.

---

### Post by TheSavage on 2005-10-03
You can also try this [Kiso]("http://kiso.sourceforge.net/index.php")

---

### Post by mlomker on 2005-10-03
> [Kiso]("http://kiso.sourceforge.net/index.php")

I personally prefer the scripts because once mounted you can use any tool/file manager with them.  It also looks like it's just for ISO.

---

### Post by daller on 2005-10-03
Shouldn't it works with this file???

-rwxrwxrwt   1 daniel root 12533 2005-09-28 17:20 kompas.iso

Is it a problem with the mount-directory - maybe???

---

### Post by daller on 2005-10-03
Not that I find the KIso-project that attractive, but i'm willing to give it a try...

Compiling it, gives me this:

checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!

...I have build-essential installed - anything else?

---

### Post by mlomker on 2005-10-03
libx11-dev and kde-devel I'd imagine.

---

### Post by GTvulse on 2005-10-03
[QUOTE=daller]Hi All,

How do I mount an ISO or CUE/BIN file?

A commandline-solution is O.K. - but what i'm searching for, is a GUI app!

thanks![/QUOTE]
Probably the easiest way to mount an ISO image is the old skool :-):

```
mount -t iso9660 -o ro,loop the_cd_image.iso /mount/point
```

If you use Gnome and mount it in a directory inside /media, you'll have a nice mounted volume on your desktop. To create empty ISO images you can write to, you can use mkisofs.

---

### Post by mlomker on 2005-10-03
> 
If you use Gnome and mount it in a directory inside /media, you'll have a nice mounted volume on your desktop. To create empty ISO images you can write to, you can use mkisofs.

That is exactly what the script does.  It just makes it convenient.

---

### Post by GTvulse on 2005-10-04
[QUOTE=mlomker]That is exactly what the script does.  It just makes it convenient.[/QUOTE]
Give a man a fish and he will eat one day; teach a man to fish and he will eat every day...

---

### Post by daller on 2005-10-04
Exactly the way I wanna learn stuff...

...It's pretty good to know commands for most things - but for daily use, a GUI is "better"!

---

### Post by daller on 2005-10-04
During "sudo make install" it runs into some problems: (fejl = error)

kiso.cpp:3412: fejl: 'ommodus' was not declared in this scope
kiso.cpp:3412: fejl: 'cdio_is_discmode_dvd' was not declared in this scope
kiso.cpp:3417: fejl: 'cdio_eject_media' was not declared in this scope
kiso.cpp:3418: fejl: 'cdio_destroy' was not declared in this scope
kiso.cpp: In member function 'virtual void Mainform::showdrive()':
kiso.cpp:3570: fejl: 'CdIo' was not declared in this scope
kiso.cpp:3570: fejl: 'p_cdio' was not declared in this scope
kiso.cpp:3573: fejl: 'cdio_hwinfo_t' was not declared in this scope
kiso.cpp:3573: fejl: expected `;' before 'p_hw_info'
kiso.cpp:3574: fejl: 'DRIVER_DEVICE' was not declared in this scope
kiso.cpp:3574: fejl: 'cdio_open' was not declared in this scope
kiso.cpp:3577: fejl: 'track_t' was not declared in this scope
kiso.cpp:3577: fejl: expected `;' before 'num_tracks'
kiso.cpp:3578: fejl: expected `;' before 'first_track_num'
kiso.cpp:3579: fejl: 'discmode_t' was not declared in this scope
kiso.cpp:3579: fejl: expected `;' before 'ommodus'
kiso.cpp:3580: fejl: 'p_hw_info' was not declared in this scope
kiso.cpp:3580: fejl: 'cdio_get_hwinfo' was not declared in this scope
kiso.cpp:3583: fejl: 'msf_t' was not declared in this scope
kiso.cpp:3583: fejl: expected `;' before 'msf'
kiso.cpp:3584: fejl: 'CDIO_CDROM_LEADOUT_TRACK' was not declared in this scope
kiso.cpp:3584: fejl: 'msf' was not declared in this scope
kiso.cpp:3584: fejl: 'cdio_get_track_msf' was not declared in this scope
kiso.cpp:3585: fejl: 'lsn_t' was not declared in this scope
kiso.cpp:3585: fejl: expected `;' before 'lsn'
kiso.cpp:3586: fejl: 'lsn' was not declared in this scope
kiso.cpp:3586: fejl: 'CDIO_CD_FRAMESIZE_RAW' was not declared in this scope
kiso.cpp:3587: fejl: 'first_track_num' was not declared in this scope
kiso.cpp:3587: fejl: 'num_tracks' was not declared in this scope
kiso.cpp:3589: fejl: 'TRACK_FORMAT_AUDIO' was not declared in this scope
kiso.cpp:3589: fejl: 'cdio_get_track_format' was not declared in this scope
kiso.cpp:3591: fejl: 'TRACK_FORMAT_DATA' was not declared in this scope
kiso.cpp:3591: fejl: 'cdio_get_track_format' was not declared in this scope
kiso.cpp:3594: fejl: 'cdio_drive_read_cap_t' was not declared in this scope
kiso.cpp:3594: fejl: expected `;' before 'i_read_cap'
kiso.cpp:3595: fejl: 'cdio_drive_write_cap_t' was not declared in this scope
kiso.cpp:3595: fejl: expected `;' before 'i_write_cap'
kiso.cpp:3596: fejl: 'cdio_drive_misc_cap_t' was not declared in this scope
kiso.cpp:3596: fejl: expected `;' before 'i_misc_cap'
kiso.cpp:3602: fejl: 'scsi_mmc_cdb_t' was not declared in this scope
kiso.cpp:3602: fejl: expected `;' before 'cdb'
kiso.cpp:3604: fejl: 'cdb' was not declared in this scope
kiso.cpp:3604: fejl: 'CDIO_MMC_GPCMD_GET_CONFIGURATION' was not declared in this scope
kiso.cpp:3604: fejl: 'CDIO_MMC_SET_COMMAND' was not declared in this scope
kiso.cpp:3605: fejl: 'CDIO_MMC_SET_READ_LENGTH8' was not declared in this scope
kiso.cpp:3606: fejl: 'CDIO_MMC_GET_CONF_ALL_FEATURES' was not declared in this scope
kiso.cpp:3609: fejl: 'SCSI_MMC_DATA_READ' was not declared in this scope
kiso.cpp:3609: fejl: 'scsi_mmc_run_cmd' was not declared in this scope
kiso.cpp:3615: fejl: 'CDIO_MMC_GET_LEN32' was not declared in this scope
kiso.cpp:3621: fejl: 'CDIO_MMC_GET_LEN16' was not declared in this scope
kiso.cpp:3625: fejl: 'CDIO_MMC_FEATURE_CORE' was not declared in this scope
kiso.cpp:3656: fejl: 'ommodus' was not declared in this scope
kiso.cpp:3656: fejl: 'cdio_is_discmode_cdrom' was not declared in this scope
kiso.cpp:3657: fejl: 'ommodus' was not declared in this scope
kiso.cpp:3657: fejl: 'CDIO_DISC_MODE_DVD_R' was not declared in this scope
kiso.cpp:3658: fejl: 'ommodus' was not declared in this scope
kiso.cpp:3658: fejl: 'CDIO_DISC_MODE_DVD_RW' was not declared in this scope
kiso.cpp:3659: fejl: 'ommodus' was not declared in this scope
kiso.cpp:3659: fejl: 'CDIO_DISC_MODE_DVD_R' was not declared in this scope
kiso.cpp:3660: fejl: 'ommodus' was not declared in this scope
kiso.cpp:3660: fejl: 'CDIO_DISC_MODE_DVD_ROM' was not declared in this scope
kiso.cpp:3661: fejl: 'ommodus' was not declared in this scope
kiso.cpp:3661: fejl: 'CDIO_DISC_MODE_DVD_RAM' was not declared in this scope
kiso.cpp:3662: fejl: 'ommodus' was not declared in this scope
kiso.cpp:3662: fejl: 'CDIO_DISC_MODE_CD_DA' was not declared in this scope
kiso.cpp:3663: fejl: 'i_read_cap' was not declared in this scope
kiso.cpp:3663: fejl: 'i_write_cap' was not declared in this scope
kiso.cpp:3663: fejl: 'i_misc_cap' was not declared in this scope
kiso.cpp:3663: fejl: 'cdio_get_drive_cap_dev' was not declared in this scope
kiso.cpp:3664: fejl: 'CDIO_DRIVE_CAP_READ_DVD_ROM' was not declared in this scope
kiso.cpp:3665: fejl: 'CDIO_DRIVE_CAP_WRITE_CD_R' was not declared in this scope
kiso.cpp:3666: fejl: 'CDIO_DRIVE_CAP_WRITE_CD_RW' was not declared in this scope
kiso.cpp:3667: fejl: 'CDIO_DRIVE_CAP_WRITE_DVD_R' was not declared in this scope
kiso.cpp:3668: fejl: 'CDIO_DRIVE_CAP_WRITE_DVD_RW' was not declared in this scope
kiso.cpp:3674: fejl: 'cdio_destroy' was not declared in this scope
kiso.cpp: In member function 'virtual int Mainform::ProgressBar(QString, QString, KShellProcess*, double)':
kiso.cpp:3684: fejl: 'lba_t' was not declared in this scope
kiso.cpp:3684: fejl: expected `;' before 'first_audio_lba'
kiso.cpp:3687: fejl: 'CdIo' was not declared in this scope
kiso.cpp:3687: fejl: 'cdio' was not declared in this scope
kiso.cpp:3687: fejl: 'cdio_open_cd' was not declared in this scope
kiso.cpp:3688: fejl: 'track_t' was not declared in this scope
kiso.cpp:3688: fejl: expected `;' before 'num_tracks'
kiso.cpp:3689: fejl: expected `;' before 'first_track_num'
kiso.cpp:3690: fejl: 'first_track_num' was not declared in this scope
kiso.cpp:3690: fejl: 'num_tracks' was not declared in this scope
kiso.cpp:3691: fejl: 'TRACK_FORMAT_AUDIO' was not declared in this scope
kiso.cpp:3691: fejl: 'cdio_get_track_format' was not declared in this scope
kiso.cpp:3692: fejl: 'first_audio_lba' was not declared in this scope
kiso.cpp:3693: fejl: 'cdio_get_track_lba' was not declared in this scope
kiso.cpp:3697: fejl: 'cdio_stat_size' was not declared in this scope
kiso.cpp:3698: fejl: 'cdio_destroy' was not declared in this scope
make[1]: *** [kiso.o] Error 1
make[1]: Leaving directory '/home/daniel/downloads/kiso-0.8.2/src'
make: *** [install-recursive] Error 1

---

### Post by mlomker on 2005-10-04
> Give a man a fish and he will eat one day; teach a man to fish and he will eat every day...

I go to the supermarket.  I don't have time for fishing. ;)


Edit:  Added the emoticon--this was meant as a joke!

---

### Post by mlomker on 2005-10-04
> During "sudo make install" it runs into some problems: (fejl = error)


I tried a couple versions and could not get it to compile, either.

---

### Post by daller on 2005-10-07
Well, then it's not because i'm dumb :)

...Guess i'll have to wait then - Simply looks like a nice game!

---

### Post by BoyOfDestiny on 2005-10-07
After 3 secs. of googling found this.

[http://kde-apps.org/content/show.php?content=11577](http://kde-apps.org/content/show.php?content=11577)

Anyone know about gnome equivalent?

---

### Post by daller on 2005-10-11
Well, can't manage to install cdemu...

#*#  2  #*#
you need the source of your current running kernel.
/lib/modules/`uname -r`/build/include needs to point at it. if you're not sure if it points
to the righ kernel just type: ls -la /lib/modules/`uname -r`/build if its the correct kernel
source all is ok. ;-)

#*#*#*#*#*#

daniel@dallap:~$ ls -la /lib/modules/`uname -r`/build
ls: /lib/modules/2.6.12-9-386/build: No such file or directory!

I've run apt-get source on these:

linux-headers-2.6.12-9-386 - Linux kernel headers 2.6.12 on 386
linux-image-2.6.12-9-386 - Linux kernel image for version 2.6.12 on 386.
linux-restricted-modules-2.6.12-9-386 - Non-free Linux 2.6.12 modules on 386

Still not working!

daniel@dallap:~$ cd /lib/modules/2.6.12-9-386/
initrd/              modules.dep          modules.seriomap
kernel/              modules.ieee1394map  modules.symbols
madwifi/             modules.inputmap     modules.usbmap
modules.alias        modules.isapnpmap    volatile/
modules.ccwmap       modules.pcimap

.../build is missing!!!

How is that accomplished? - easily!

---

