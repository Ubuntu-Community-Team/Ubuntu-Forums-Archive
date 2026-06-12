---
title: "compiling kiso probs"
date: 2005-10-26
forum: Desktop Environments
---

### Post by stoeptegel on 2005-10-26
After installing the packages xlibs-dev, libqt3-mt-dev, kdelibs and kdelibs4-dev i came through ./configure
so i was excited and did 'make' :-)  Which gave me the following (long) error:

```
make[2]: Entering directory `/home/mvv/used.soft/kiso-0.8.2/src'
if g++ -DHAVE_CONFIG_H -I. -I. -I.. -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wnon-virtual-dtor -Wno-long-long -Wundef -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-subscripts -Wall -W -Wpointer-arith -Wwrite-strings -O2 -Wformat-security -Wmissing-format-attribute -fno-exceptions -fno-check-new -fno-common  -MT kiso.o -MD -MP -MF ".deps/kiso.Tpo" -c -o kiso.o kiso.cpp; \
then mv -f ".deps/kiso.Tpo" ".deps/kiso.Po"; else rm -f ".deps/kiso.Tpo"; exit 1; fi
kiso.cpp:14:23: fout: cdio/cdio.h: Onbekend bestand of map
kiso.cpp:15:22: fout: cdio/mmc.h: Onbekend bestand of map
/usr/share/qt3/include/qtooltip.h:86: let op: ‘class QToolTip’ has virtual functions but non-virtual destructor
/usr/include/kde/kfiletreeview.h:41: let op: ‘class KFileTreeViewToolTip’ has virtual functions but non-virtual destructor
/usr/include/kde/keditlistbox.h:59: let op: ‘class KEditListBox::CustomEditor’ has virtual functions but non-virtual destructor
kiso.cpp: In member function ‘virtual void Mainform::choice()’:
kiso.cpp:3179: fout: ‘CdIo’ was not declared in this scope
kiso.cpp:3179: fout: ‘cdio’ was not declared in this scope
kiso.cpp:3179: fout: ‘cdio_open_cd’ was not declared in this scope
kiso.cpp:3181: fout: ‘track_t’ was not declared in this scope
kiso.cpp:3181: fout: expected `;' before ‘num_tracks’
kiso.cpp:3182: fout: expected `;' before ‘first_track_num’
kiso.cpp:3187: fout: ‘first_track_num’ was not declared in this scope
kiso.cpp:3187: fout: ‘cdio_get_first_track_num’ was not declared in this scope
kiso.cpp:3188: fout: ‘num_tracks’ was not declared in this scope
kiso.cpp:3188: fout: ‘cdio_get_num_tracks’ was not declared in this scope
kiso.cpp:3189: fout: ‘TRACK_FORMAT_AUDIO’ was not declared in this scope
kiso.cpp:3189: fout: ‘cdio_get_track_format’ was not declared in this scope
kiso.cpp:3191: fout: ‘cdio_destroy’ was not declared in this scope
kiso.cpp:3194: fout: ‘TRACK_FORMAT_AUDIO’ was not declared in this scope
kiso.cpp:3194: fout: ‘cdio_get_track_format’ was not declared in this scope
kiso.cpp:3197: fout: ‘cdio_destroy’ was not declared in this scope
kiso.cpp: In member function ‘virtual void Mainform::createiso(QString)’:
kiso.cpp:3367: fout: ‘CdIo’ was not declared in this scope
kiso.cpp:3367: fout: ‘cdio’ was not declared in this scope
kiso.cpp:3367: fout: ‘cdio_open_cd’ was not declared in this scope
kiso.cpp:3368: fout: ‘discmode_t’ was not declared in this scope
kiso.cpp:3368: fout: expected `;' before ‘ommodus’
kiso.cpp:3369: fout: ‘ommodus’ was not declared in this scope
kiso.cpp:3369: fout: ‘cdio_is_discmode_dvd’ was not declared in this scope
kiso.cpp:3371: fout: ‘cdio_stat_size’ was not declared in this scope
kiso.cpp:3373: fout: ‘CDIO_CD_FRAMESIZE_RAW’ was not declared in this scope
kiso.cpp:3374: fout: ‘CDIO_CD_FRAMESIZE’ was not declared in this scope
kiso.cpp:3376: fout: ‘track_t’ was not declared in this scope
kiso.cpp:3376: fout: expected `;' before ‘num_tracks’
kiso.cpp:3378: fout: ‘lsn_t’ was not declared in this scope
kiso.cpp:3378: fout: expected `;' before ‘leadoutlsn’
kiso.cpp:3379: fout: expected `;' before ‘actuallsn’
kiso.cpp:3380: fout: expected `;' before ‘lastlsn’
kiso.cpp:3381: fout: ‘leadoutlsn’ was not declared in this scope
kiso.cpp:3381: fout: ‘CDIO_CDROM_LEADOUT_TRACK’ was not declared in this scope
kiso.cpp:3381: fout: ‘cdio_get_track_lsn’ was not declared in this scope
kiso.cpp:3382: fout: ‘lastlsn’ was not declared in this scope
kiso.cpp:3383: fout: ‘num_tracks’ was not declared in this scope
kiso.cpp:3383: fout: ‘cdio_get_num_tracks’ was not declared in this scope
kiso.cpp:3385: fout: ‘TRACK_FORMAT_AUDIO’ was not declared in this scope
kiso.cpp:3385: fout: ‘cdio_get_track_format’ was not declared in this scope
kiso.cpp:3387: fout: ‘cdio_get_track_lba’ was not declared in this scope
kiso.cpp:3393: fout: ‘actuallsn’ was not declared in this scope
kiso.cpp:3395: fout: ‘buffer’ was not declared in this scope
kiso.cpp:3395: fout: ‘cdio_read_mode1_sector’ was not declared in this scope
kiso.cpp:3396: fout: no matching function for call to ‘QFile::writeBlock(<type error>, unsigned int&)’
/usr/share/qt3/include/qfile.h:85: note: candidates are: virtual Q_LONG QFile::writeBlock(const char*, Q_ULONG)
/usr/share/qt3/include/qfile.h:86: note:                 Q_LONG QFile::writeBlock(const QByteArray&)
kiso.cpp:3407: fout: ‘buffer’ was not declared in this scope
kiso.cpp:3407: fout: ‘cdio_read_mode1_sector’ was not declared in this scope
kiso.cpp:3408: fout: no matching function for call to ‘QFile::writeBlock(<type error>, unsigned int&)’
/usr/share/qt3/include/qfile.h:85: note: candidates are: virtual Q_LONG QFile::writeBlock(const char*, Q_ULONG)
/usr/share/qt3/include/qfile.h:86: note:                 Q_LONG QFile::writeBlock(const QByteArray&)
kiso.cpp:3412: fout: ‘ommodus’ was not declared in this scope
kiso.cpp:3412: fout: ‘cdio_is_discmode_dvd’ was not declared in this scope
kiso.cpp:3417: fout: ‘cdio_eject_media’ was not declared in this scope
kiso.cpp:3418: fout: ‘cdio_destroy’ was not declared in this scope
kiso.cpp: In member function ‘virtual void Mainform::showdrive()’:
kiso.cpp:3570: fout: ‘CdIo’ was not declared in this scope
kiso.cpp:3570: fout: ‘p_cdio’ was not declared in this scope
kiso.cpp:3573: fout: ‘cdio_hwinfo_t’ was not declared in this scope
kiso.cpp:3573: fout: expected `;' before ‘p_hw_info’
kiso.cpp:3574: fout: ‘DRIVER_DEVICE’ was not declared in this scope
kiso.cpp:3574: fout: ‘cdio_open’ was not declared in this scope
kiso.cpp:3577: fout: ‘track_t’ was not declared in this scope
kiso.cpp:3577: fout: expected `;' before ‘num_tracks’
kiso.cpp:3578: fout: expected `;' before ‘first_track_num’
kiso.cpp:3579: fout: ‘discmode_t’ was not declared in this scope
kiso.cpp:3579: fout: expected `;' before ‘ommodus’
kiso.cpp:3580: fout: ‘p_hw_info’ was not declared in this scope
kiso.cpp:3580: fout: ‘cdio_get_hwinfo’ was not declared in this scope
kiso.cpp:3583: fout: ‘msf_t’ was not declared in this scope
kiso.cpp:3583: fout: expected `;' before ‘msf’
kiso.cpp:3584: fout: ‘CDIO_CDROM_LEADOUT_TRACK’ was not declared in this scope
kiso.cpp:3584: fout: ‘msf’ was not declared in this scope
kiso.cpp:3584: fout: ‘cdio_get_track_msf’ was not declared in this scope
kiso.cpp:3585: fout: ‘lsn_t’ was not declared in this scope
kiso.cpp:3585: fout: expected `;' before ‘lsn’
kiso.cpp:3586: fout: ‘lsn’ was not declared in this scope
kiso.cpp:3586: fout: ‘CDIO_CD_FRAMESIZE_RAW’ was not declared in this scope
kiso.cpp:3587: fout: ‘first_track_num’ was not declared in this scope
kiso.cpp:3587: fout: ‘num_tracks’ was not declared in this scope
kiso.cpp:3589: fout: ‘TRACK_FORMAT_AUDIO’ was not declared in this scope
kiso.cpp:3589: fout: ‘cdio_get_track_format’ was not declared in this scope
kiso.cpp:3591: fout: ‘TRACK_FORMAT_DATA’ was not declared in this scope
kiso.cpp:3591: fout: ‘cdio_get_track_format’ was not declared in this scope
kiso.cpp:3594: fout: ‘cdio_drive_read_cap_t’ was not declared in this scope
kiso.cpp:3594: fout: expected `;' before ‘i_read_cap’
kiso.cpp:3595: fout: ‘cdio_drive_write_cap_t’ was not declared in this scope
kiso.cpp:3595: fout: expected `;' before ‘i_write_cap’
kiso.cpp:3596: fout: ‘cdio_drive_misc_cap_t’ was not declared in this scope
kiso.cpp:3596: fout: expected `;' before ‘i_misc_cap’
kiso.cpp:3602: fout: ‘scsi_mmc_cdb_t’ was not declared in this scope
kiso.cpp:3602: fout: expected `;' before ‘cdb’
kiso.cpp:3604: fout: ‘cdb’ was not declared in this scope
kiso.cpp:3604: fout: ‘CDIO_MMC_GPCMD_GET_CONFIGURATION’ was not declared in this scope
kiso.cpp:3604: fout: ‘CDIO_MMC_SET_COMMAND’ was not declared in this scope
kiso.cpp:3605: fout: ‘CDIO_MMC_SET_READ_LENGTH8’ was not declared in this scope
kiso.cpp:3606: fout: ‘CDIO_MMC_GET_CONF_ALL_FEATURES’ was not declared in this scope
kiso.cpp:3609: fout: ‘SCSI_MMC_DATA_READ’ was not declared in this scope
kiso.cpp:3609: fout: ‘scsi_mmc_run_cmd’ was not declared in this scope
kiso.cpp:3615: fout: ‘CDIO_MMC_GET_LEN32’ was not declared in this scope
kiso.cpp:3621: fout: ‘CDIO_MMC_GET_LEN16’ was not declared in this scope
kiso.cpp:3625: fout: ‘CDIO_MMC_FEATURE_CORE’ was not declared in this scope
kiso.cpp:3656: fout: ‘ommodus’ was not declared in this scope
kiso.cpp:3656: fout: ‘cdio_is_discmode_cdrom’ was not declared in this scope
kiso.cpp:3657: fout: ‘ommodus’ was not declared in this scope
kiso.cpp:3657: fout: ‘CDIO_DISC_MODE_DVD_R’ was not declared in this scope
kiso.cpp:3658: fout: ‘ommodus’ was not declared in this scope
kiso.cpp:3658: fout: ‘CDIO_DISC_MODE_DVD_RW’ was not declared in this scope
kiso.cpp:3659: fout: ‘ommodus’ was not declared in this scope
kiso.cpp:3659: fout: ‘CDIO_DISC_MODE_DVD_R’ was not declared in this scope
kiso.cpp:3660: fout: ‘ommodus’ was not declared in this scope
kiso.cpp:3660: fout: ‘CDIO_DISC_MODE_DVD_ROM’ was not declared in this scope
kiso.cpp:3661: fout: ‘ommodus’ was not declared in this scope
kiso.cpp:3661: fout: ‘CDIO_DISC_MODE_DVD_RAM’ was not declared in this scope
kiso.cpp:3662: fout: ‘ommodus’ was not declared in this scope
kiso.cpp:3662: fout: ‘CDIO_DISC_MODE_CD_DA’ was not declared in this scope
kiso.cpp:3663: fout: ‘i_read_cap’ was not declared in this scope
kiso.cpp:3663: fout: ‘i_write_cap’ was not declared in this scope
kiso.cpp:3663: fout: ‘i_misc_cap’ was not declared in this scope
kiso.cpp:3663: fout: ‘cdio_get_drive_cap_dev’ was not declared in this scope
kiso.cpp:3664: fout: ‘CDIO_DRIVE_CAP_READ_DVD_ROM’ was not declared in this scope
kiso.cpp:3665: fout: ‘CDIO_DRIVE_CAP_WRITE_CD_R’ was not declared in this scope
kiso.cpp:3666: fout: ‘CDIO_DRIVE_CAP_WRITE_CD_RW’ was not declared in this scope
kiso.cpp:3667: fout: ‘CDIO_DRIVE_CAP_WRITE_DVD_R’ was not declared in this scope
kiso.cpp:3668: fout: ‘CDIO_DRIVE_CAP_WRITE_DVD_RW’ was not declared in this scope
kiso.cpp:3674: fout: ‘cdio_destroy’ was not declared in this scope
kiso.cpp: In member function ‘virtual int Mainform::ProgressBar(QString, QString, KShellProcess*, double)’:
kiso.cpp:3684: fout: ‘lba_t’ was not declared in this scope
kiso.cpp:3684: fout: expected `;' before ‘first_audio_lba’
kiso.cpp:3687: fout: ‘CdIo’ was not declared in this scope
kiso.cpp:3687: fout: ‘cdio’ was not declared in this scope
kiso.cpp:3687: fout: ‘cdio_open_cd’ was not declared in this scope
kiso.cpp:3688: fout: ‘track_t’ was not declared in this scope
kiso.cpp:3688: fout: expected `;' before ‘num_tracks’
kiso.cpp:3689: fout: expected `;' before ‘first_track_num’
kiso.cpp:3690: fout: ‘first_track_num’ was not declared in this scope
kiso.cpp:3690: fout: ‘num_tracks’ was not declared in this scope
kiso.cpp:3691: fout: ‘TRACK_FORMAT_AUDIO’ was not declared in this scope
kiso.cpp:3691: fout: ‘cdio_get_track_format’ was not declared in this scope
kiso.cpp:3692: fout: ‘first_audio_lba’ was not declared in this scope
kiso.cpp:3693: fout: ‘cdio_get_track_lba’ was not declared in this scope
kiso.cpp:3697: fout: ‘cdio_stat_size’ was not declared in this scope
kiso.cpp:3698: fout: ‘cdio_destroy’ was not declared in this scope
make[2]: *** [kiso.o] Fout 1
make[2]: Leaving directory `/home/mvv/used.soft/kiso-0.8.2/src'
make[1]: *** [all-recursive] Fout 1
make[1]: Leaving directory `/home/mvv/used.soft/kiso-0.8.2'
make: *** [all] Fout 2
```

I hope there is someone with a clue how to fix this.

---

### Post by gerdasche on 2005-10-31
sorry for the late answer! try the deb-files i found, they work fine for me!
[libcdio3_0.81-2c-1_i386.deb]("http://www.podulator.com/debs/kiso/libcdio3_0.81-2c-1_i386.deb")
[kiso_0.8.2-1_i386.deb]("http://www.podulator.com/debs/kiso/kiso_0.8.2-1_i386.deb")
 

bye

---

### Post by daller on 2005-11-01
Where is a virtual drive mounted?

...Can't seem to get it to work!

---

### Post by stoeptegel on 2005-11-01
Thanks gerdasche, i'll try them tomorrow :)

---

### Post by N6546R on 2005-11-01
Looks like it's missing a header file from one on the dependencies. Did you install the -dev packages of them?

Perry

---

### Post by stoeptegel on 2005-11-02
Sry i dunno N6546R, i was forced to do a clean install... thanks though.

---

### Post by stoeptegel on 2005-11-03
With the debian package i get:

$ kiso```

kiso: error while loading shared libraries: libiso9660.so.4: cannot open shared object file: No such file or directory
```

---

### Post by N6546R on 2005-11-03
Here's a link to libiso9660-4:
[http://packages.debian.org/unstable/libs/libiso9660-4](http://packages.debian.org/unstable/libs/libiso9660-4)

Note that I don't know what dependencies might be broken by installing this package.

Perry

[QUOTE=stoeptegel]With the debian package i get:

$ kiso```

kiso: error while loading shared libraries: libiso9660.so.4: cannot open shared object file: No such file or directory
```[/QUOTE]

---

### Post by stoeptegel on 2005-11-03
ai packages from debian.org, that's what killed my machine this week already. I think i'll choose for safety and wait for an ubuntu package.

---

### Post by stoeptegel on 2005-11-11
I've got the klik://kiso version working now. :p :KS

---

