---
title: "I don't have write access to my DVD burner??"
date: 2006-02-01
forum: Desktop Environments
---

### Post by catalytic on 2006-02-01
I was just trying to burn a file to a DVD-RW disc and it just wont work.

All it says is: 
There was an error writing to the disc:
Unhandled error, aborting

When I look in my DVD drive properties I notice that I don't have write permission.

How do I fix this? I do currently have data on the disc, it asks if I want to erase, yet I get no further than this. Also is there another way to burn other than nautilus?

 PLEASE HELP!! The file I'm actually trying to burn is Quake 3 demo for windows, as windows can't access the internet anymore, I needed to run the installer in windows. 
This is another problem I am having, I can't get any games to work on linux only the crappy ones that you get through synaptic. I have WOW on my windows partition it wont play in linux. I have tried installing windows games to my linux partition, they don't work. So I was going to try installing in windows and then playing in Linux. As the whole point is I want to play an online game! Though this is also a mission as I only have crappy on board graphics not capable of 3D. Yes I know time to upgrade...

---

### Post by catalytic on 2006-02-01
I have also followed the starter guide to blank the DVD this is what I get

root@ubuntu:~# sudo umount /dev/cdrom
umount: /dev/cdrom: not mounted
root@ubuntu:~# cdrecord dev=/dev/cdrom blank=fast
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

cdrecord: Warning: Running on Linux-2.6.12-10-386
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '/dev/cdrom'
devname: '/dev/cdrom'
scsibus: -2 target: -2 lun: -2
Warning: Open by 'devname' is unintentional and not supported.
Linux sg driver version: 3.5.27
Using libscg version 'ubuntu-0.8ubuntu1'.
cdrecord: Warning: using inofficial version of libscg (ubuntu-0.8ubuntu1 '@(#)scsitransp.c      1.91 04/06/17 Copyright 1988,1995,2000-2004 J. Schilling').
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   :
Vendor_info    : 'HL-DT-ST'
Identifikation : 'DVDRAM GSA-4160B'
Revision       : 'A301'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
cdrecord: Found DVD media but DVD-R/DVD-RW support code is missing.
cdrecord: If you need DVD-R/DVD-RW support, ask the Author for cdrecord-ProDVD.
cdrecord: Free test versions and free keys for personal use are at [ftp://ftp.berlios.de/pub/cdrecord/ProDVD/](ftp://ftp.berlios.de/pub/cdrecord/ProDVD/)
cdrecord: This version of cdrecord does not include DVD-R/DVD-RW support code.
cdrecord: See /usr/share/doc/cdrecord/README.DVD.Debian for details on DVD support.
Using generic SCSI-3/mmc   CD/DVD driver (checks media) (mmc_cd_dvd).
Driver flags   : MMC-3 SWABAUDIO BURNFREE
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Starting to write CD/DVD at speed 15 in real BLANK mode for single session.
Last chance to quit, starting real write    0 seconds. Operation starts.
This drive or media does not support the 'BLANK media' command
cdrecord: Cannot blank disk, aborting.
cdrecord: Some drives do not support all blank types.
cdrecord: Try again with cdrecord blank=all.

---

### Post by catalytic on 2006-02-01
I have also tried dvdrtools, but I can't figure out how to use it
root@ubuntu:~# dvdrtools
bash: dvdrtools: command not found

But dvdrecord returns this

root@ubuntu:~# dvdrecord
dvdrecord: No CD/DVD-Recorder device specified.
dvdrecord: Usage: dvdrecord [options] track1...trackn
Options:
        -version        print version information and exit
        dev=target      SCSI target to use as CD/DVD-Recorder
        timeout=#       set the default SCSI command timeout to #.
        debug=#,-d      Set to # or increment misc debug level
        kdebug=#,kd=#   do Kernel debugging
        -verbose,-v     increment general verbose level by one
        -Verbose,-V     increment SCSI command transport verbose level by one
        -silent,-s      do not print status of failed SCSI commands
        driver=name     user supplied driver name, use with extreme care
        driveropts=opt  a comma separated list of driver specific options
        -checkdrive     check if a driver for the drive is present
        -prcap          print drive capabilities for MMC compliant drives
        -inq            do an inquiry for the drive and exit
        -scanbus        scan the SCSI bus and exit
        -reset          reset the SCSI bus with the cdrecorder (if possible)
        -overburn       allow to write more than the official size of a medium
        -ignsize        ignore the known size of a medium (may cause problems)
        -useinfo        use *.inf files to overwrite audio options.
        speed=#         set speed of drive
        blank=type      blank a CD-RW disc (see blank=help)
        fs=#            Set fifo size to # (0 to disable, default is 4 MB)
        -load           load the disk and exit (works only with tray loader)
        -eject          eject the disk after doing the work
        -dummy          do everything with laser turned off
        -msinfo         retrieve multi-session info for mkisofs >= 1.10
        -toc            retrieve and print TOC/PMA data
        -atip           retrieve and print ATIP data
        -multi          generate a TOC that allows multi session
                        In this case default track type is CD-ROM XA2
        -fix            fixate a corrupt or unfixated disk (generate a TOC)
        -nofix          do not fixate disk after writing tracks
        -waiti          wait until input is available before opening SCSI
        -force          force to continue on some errors to allow blanking bad disks
        -dao            Write disk in DAO mode. This option will be replaced in the future.
        -raw            Write disk in RAW mode. This option will be replaced in the future.
        -raw96r         Write disk in RAW/RAW96R mode. This option will be replaced in the future.
        -raw96p         Write disk in RAW/RAW96P mode. This option will be replaced in the future.
        -raw16          Write disk in RAW/RAW16 mode. This option will be replaced in the future.
        tsize=#         Length of valid data in next track
        padsize=#       Amount of padding for next track
        pregap=#        Amount of pre-gap sectors before next track
        defpregap=#     Amount of pre-gap sectors for all but track #1
        mcn=text        Set the media catalog number for this CD to 'text'
        isrc=text       Set the ISRC number for the next track to 'text'
        index=list      Set the index list for the next track to 'list'
        -text           Write CD-Text from information from *.inf files
        textfile=name   Set the file with CD-Text data to 'name'
        -audio          Subsequent tracks are CD-DA audio tracks
        -data           Subsequent tracks are CD-ROM data mode 1 (default)
        -mode2          Subsequent tracks are CD-ROM data mode 2
        -xa1            Subsequent tracks are CD-ROM XA mode 1
        -xa2            Subsequent tracks are CD-ROM XA mode 2
        -cdi            Subsequent tracks are CDI tracks
        -isosize        Use iso9660 file system size for next data track
        -preemp         Audio tracks are mastered with 50/15 &#65535;s preemphasis
        -nopreemp       Audio tracks are mastered with no preemphasis (default)
        -copy           Audio tracks have unlimited copy permission
        -nocopy         Audio tracks may only be copied once for personal use (default)
        -scms           Audio tracks willl not not have any copy permission at all
        -pad            Pad data tracks with 15 zeroed sectors
                        Pad audio tracks to a multiple of 2352 bytes
        -nopad          Do not pad data tracks (default)
        -shorttrack     Subsequent tracks may be non Red Book < 4 seconds if in DAO mode
        -noshorttrack   Subsequent tracks must be >= 4 seconds
        -swab           Audio data source is byte-swapped (little-endian/Intel)
        -gui            Make output more GUI- (and less human-) readable
        -delay x        Set delay before writing to x seconds (default: 9)
The type of the first track is used for the toc type.
Currently only form 1 tracks are supported.


Please someone help, I have been sitting here for 2 hours trying to figure this out...

---

### Post by classem2003 on 2006-02-01
To burn cd with nautilus is a bit hard for me. Usually I use k3b. It has a nice interface. You can get it with synaptic if the universe and multiverse repositories are active. Before downloading, go to preferences and then, in one of those tabs check the option, consider "consider recommended packages as dependencies". And that's it.

---

### Post by catalytic on 2006-02-01
[QUOTE=classem2003]To burn cd with nautilus is a bit hard for me. Usually I use k3b. It has a nice interface. You can get it with synaptic if the universe and multiverse repositories are active. Before downloading, go to preferences and then, in one of those tabs check the option, consider "consider recommended packages as dependencies". And that's it.[/QUOTE]
Thanks I'll try that, but does this also allow the option to erase a dvd?

---

### Post by catalytic on 2006-02-01
[QUOTE=catalytic]Thanks I'll try that, but does this also allow the option to erase a dvd?[/QUOTE]
Seems to work, thank you for that.

---

