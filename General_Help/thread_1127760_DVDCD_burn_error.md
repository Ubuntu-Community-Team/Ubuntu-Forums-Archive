---
title: "DVD/CD burn error"
date: 2009-04-16
forum: General Help
---

### Post by ons on 2009-04-16
Hello,

So I open Brasero and this is the output when I try burning an .iso to a CD/DVD:
```
Checking session consistency (brasero_burn_check_session_consistency burn.c:1905)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI output set (IMAGE) image = /tmp/brasero_tmp_T1J9RU.bin toc = none
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI called brasero_job_get_input_type
BraseroBurnURI no burn:// URI found
BraseroBurnURI stopping
BraseroWodim called brasero_job_get_action
BraseroWodim getting varg
BraseroWodim called brasero_job_get_action
BraseroWodim got varg:
BraseroWodim deactivating
BraseroWodim called brasero_job_get_action
BraseroWodim getting varg
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_get_device
BraseroWodim called brasero_job_get_flags
BraseroWodim called brasero_job_get_speed
BraseroWodim called brasero_job_get_flags
BraseroWodim called brasero_job_get_input_type
BraseroWodim called brasero_job_get_fd_in
BraseroWodim called brasero_job_get_current_track
BraseroWodim called brasero_job_set_current_action
BraseroWodim got varg:
	wodim
	-v
	dev=/dev/sr1
	speed=6
	driveropts=burnfree
	-dao
	fs=16m
	-data
	-nopad
	/home/jake/Desktop/books/bt4/bt4-beta.iso
BraseroWodim Launching command
BraseroWodim called brasero_job_get_fd_out
BraseroWodim stderr: wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/sr1'
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: devname: '/dev/sr1'
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: scsibus: -2 target: -2 lun: -2
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Linux sg driver version: 3.5.27
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Wodim version: 1.1.9
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: SCSI buffer size: 64512
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: communication breaks or freezes immediately after that.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: TOC Type: 1 = CD-ROM
BraseroWodim stdout: Driveropts: 'burnfree'
BraseroWodim stdout: Device type    : Removable CD-ROM
BraseroWodim stdout: Version        : 5
BraseroWodim stdout: Response Format: 2
BraseroWodim stdout: Capabilities   : 
BraseroWodim stdout: Vendor_info    : '_NEC    '
BraseroWodim stdout: Identification : 'DVD_RW ND-3500AG'
BraseroWodim stdout: Revision       : '2.16'
BraseroWodim stdout: Device seems to be: Generic mmc2 DVD-R/DVD-RW.
BraseroWodim stdout: Current: 0x0011 (DVD-R sequential recording)
BraseroWodim stdout: Profile: 0x002B (DVD+R/DL) 
BraseroWodim stdout: Profile: 0x001B (DVD+R) 
BraseroWodim stdout: Profile: 0x001A (DVD+RW) 
BraseroWodim stdout: Profile: 0x0014 (DVD-RW sequential recording) 
BraseroWodim stdout: Profile: 0x0013 (DVD-RW restricted overwrite) 
BraseroWodim stdout: Profile: 0x0011 (DVD-R sequential recording) (current)
BraseroWodim stdout: Profile: 0x0010 (DVD-ROM) 
BraseroWodim stdout: Profile: 0x000A (CD-RW) 
BraseroWodim stdout: Profile: 0x0009 (CD-R) 
BraseroWodim stdout: Profile: 0x0008 (CD-ROM) 
BraseroWodim stdout: Using generic SCSI-3/mmc DVD-R(W) driver (mmc_mdvd).
BraseroWodim stdout: Driver flags   : SWABAUDIO BURNFREE 
BraseroWodim stdout: Supported modes: PACKET SAO
BraseroWodim stdout: Drive buf size : 1769472 = 1728 KB
BraseroWodim stdout: FIFO size      : 16777216 = 16384 KB
BraseroWodim stderr: Speed set to 8467 KB/s
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Track 01: data   854 MB        
BraseroWodim stdout: Total size:      981 MB (97:11.94) = 437396 sectors
BraseroWodim stdout: Lout start:      981 MB (97:13/71) = 437396 sectors
BraseroWodim stdout: Current Secsize: 2048
BraseroWodim stdout: HINT: use dvd+rw-mediainfo from dvd+rw-tools for information extraction.
BraseroWodim stdout: Blocks total: 2298496 Blocks current: 2298496 Blocks remaining: 1861100
BraseroWodim stdout: Starting to write CD/DVD at speed   6.0 in real SAO mode for single session.
BraseroWodim stdout: Last chance to quit, starting real write in    4 seconds.
BraseroWodim called brasero_job_set_dangerous
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout:    3 seconds.
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout:    2 seconds.
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout: 
BraseroWodim stdout:    1 seconds.   0 seconds. Operation starts.
BraseroWodim stderr: Errno: 5 (Input/output error), reserve track scsi sendcmd: no error
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: CDB:  53 00 00 00 00 00 06 AC 94 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Waiting for reader process to fill input buffer ... input buffer ready.
BraseroWodim stderr: status: 0x2 (CHECK CONDITION)
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Writing  time:    0.023s
BraseroWodim stderr: Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 30 05 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: HUP
BraseroWodim stderr: Sense Key: 0x5 Illegal Request, Segment 0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Code: 0x30 Qual 0x05 (cannot write medium - incompatible format) Fru 0x0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense flags: Blk 0 (not valid) 
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: cmd finished after 0.000s timeout 200s
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Cannot open new session.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: fifo had 255 puts and 0 gets.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: fifo was 0 times empty and 0 times full, min fill was 100%.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: HUP
BraseroWodim process finished with status 255
BraseroWodim called brasero_job_error
BraseroWodim finished with an error
BraseroWodim asked to stop because of an error
	error		= 0
	message	= "no message"
BraseroWodim stopping
BraseroWodim got killed
Session error : unknown (brasero_burn_record burn.c:2602)
```

All of the burning programs I've tried (k3b, Brasero, Gnome Baker,etc.) have failed to burn. Btw, I've tried multiple discs (DVD/CDs) from several different new CD/DVD packs. What does the aforementioned error output mean in layman's terms, and what should I do to fix the problem? (And if this same error has already been corrected in a previous thread, please link me to it, as I did not find any relevant solutions by searching forums).
ons

---

### Post by ubuntu-freak on 2009-05-23
Edit: False alarm - what I was trying to do isn't supported in Linux, so that explains the error.

---

### Post by whoop on 2009-05-23
Have you tried burning at the lowest possible speed? If you did and the problem persists I would advice you to make a bugreport about this.

---

### Post by Mojo Sapien on 2009-06-20
I got the exact same thing trying to burn an .iso of Ubuntu Studio 9.04-i386 to a DVD-R at 1x speed. I'm currently running Mint 7 (based on Ubuntu. I love Mint, but I need the audio suite and the real time kernel is just too sexy to resist!). 

The weird part is that I've burned similar .iso's (of Slackware and 64studio) using Mint and Ubuntu 8.10 with the same package of Philips discs without a hitch. I've finally decided on Ubuntu Studio, but it looks like I'll have to order a disc and wait for it.

Is there a good tutorial on bug reporting? Can't seem to find it. Getting late. Tired. G'night for now.

---

### Post by andrew.46 on 2009-06-21
Hi Mojo,

> **Mojo Sapien said:**
> I got the exact same thing trying to burn an .iso of Ubuntu Studio 9.04-i386 to a DVD-R at 1x speed.

Perhaps try the burn from the commandline:

```
growisofs -dvd-compat -Z /dev/dvd=*my_distro.iso*
```

changing the name of *my_distro.iso* to the name of your own iso of course :-).

Andrew

---

### Post by Salixman on 2009-07-05
I've been having a similar problem while trying to burn the openSUSE 11..1 iso to a dvd. I'm using a Gateway external DVD drive, and when I try to burn the image to the disc it will prepare the disc for burning. it even seems to start burning, but then it gives me an "unhandled error" message. I've downloaded it twice, as a ftp and a torrent download. I also tried the burn command, but it couldn't find the file. PS: I'm a noob.

---

### Post by andrew.46 on 2009-07-06
Hi Salixman,

> **Salixman said:**
> I also tried the burn command, but it couldn't find the file. PS: I'm a noob.

This should be a fairly easy problem to sort out. The commandline I gave anticipates that you have the terminal window open in the *same* directory as the downloaded iso. Can you give the full name of the iso and also the directory it is in?

Andrew

---

### Post by Paul_K on 2009-08-17
Andrew-

I tried the command you suggested with a couple changes because I am burning a CDR instead of a DVDR:

$ growisofs  -Z /dev/cdrw=ubuntu-9.04-desktop-i386.iso
:-( /dev/cdrw: media is not recognized as recordable DVD: 9

I get the same error message when I sudo so it doesn't seem to be a permissions issue.  I could burn CDRs or DVDRs fine before upgrading to Ubuntu 8.04 (x86 desktop)

The weird thing is If I try and burn the same iso to a DRD-R it works fine:

$ growisofs -dvd-compat -Z /dev/dvd=ubuntu-9.04-desktop-i386.iso
Executing 'builtin_dd if=ubuntu-9.04-desktop-i386.iso of=/dev/dvd obs=32k seek=0'
/dev/dvd: "Current Write Speed" is 8.2x1352KBps.
    1572864/732909568 ( 0.2%) @0.0x, remaining 46:29 RBU 100.0% UBU   2.1%
    1572864/732909568 ( 0.2%) @0.0x, remaining 77:29 RBU 100.0% UBU 100.0%
    1572864/732909568 ( 0.2%) @0.0x, remaining 100:44 RBU 100.0% UBU 100.0%
    1572864/732909568 ( 0.2%) @0.0x, remaining 123:59 RBU 100.0% UBU 100.0%
    1572864/732909568 ( 0.2%) @0.0x, remaining 154:59 RBU 100.0% UBU 100.0%
    1572864/732909568 ( 0.2%) @0.0x, remaining 178:14 RBU 100.0% UBU 100.0%
    8716288/732909568 ( 1.2%) @1.5x, remaining 36:00 RBU 100.0% UBU 100.0%
   19857408/732909568 ( 2.7%) @2.4x, remaining 17:57 RBU 100.0% UBU 100.0%
.
.  ...SNIP...
.
  680001536/732909568 (92.8%) @3.5x, remaining 0:14 RBU  99.9% UBU  89.6%
  698515456/732909568 (95.3%) @4.0x, remaining 0:09 RBU 100.0% UBU  91.7%
  717062144/732909568 (97.8%) @4.0x, remaining 0:04 RBU  47.3% UBU  91.7%
builtin_dd: 357872*2KB out @ average 2.7x1352KBps
/dev/dvd: flushing cache
/dev/dvd: closing track
/dev/dvd: closing disc 

  

Any suggestions greatly appreciated

Thanks

-PaulK



> **andrew.46 said:**
> Hi Mojo,



Perhaps try the burn from the commandline:

```
growisofs -dvd-compat -Z /dev/dvd=*my_distro.iso*
```

changing the name of *my_distro.iso* to the name of your own iso of course :-).

Andrew

---

### Post by andrew.46 on 2009-08-18
Hi Paul,

> **Paul_K said:**
> I tried the command you suggested with a couple changes because I am burning a CDR instead of a DVDR

I have not actually used growisofs for burning CDs and in fact usually use cdrecord for cd. Actually I recorded my most common usage here:

CD and DVD Writing from the Linux Command Line
[http://www.andrews-corner.org/burning.html](http://www.andrews-corner.org/burning.html)

Perhaps you might find some suitable information here? A single warning is that ubuntu does not actually use Jörg Schilling's software that I describe on this page. Ubuntu instead uses a Debian fork and this split has been endlessly and acrimoniously debated.

Andrew

---

### Post by raven on 2009-08-18
I have an issue with burning DVD ubuntu jaunty64

K3b, brasero, gnomebaker all give some error

K3b error: [ READ TRACK INFORMATION failed with SK=5h/ASC=24h/ACQ=00h]: Input/output error

brasero error: when trying to burn the iso it does not give me the burn option it stay greyed out

gnomebaker error: [ READ TRACK INFORMATION failed with SK=5h/ASC=24h/ACQ=00h]: Input/output error

tried many DVD-RW discs,  bouhgt a new DVD burner with exact same errors,
even though before, I was able to burn, now I cannot ether with jaunty nor with hardy

sudo dvd+rw-mediainfo /dev/scd0
INQUIRY:                [HL-DT-ST][DVDRAM GH22LS40 ][LL01]
GET [CURRENT] CONFIGURATION:
 Mounted Media:         14h, DVD-RW Sequential
 Media ID:              TDK601saku  
 Current Write Speed:   4.0x1385=5540KB/s
 Write Speed #0:        4.0x1385=5540KB/s
 Write Speed #1:        2.0x1385=2770KB/s
GET [CURRENT] PERFORMANCE:
 Write Performance:     4.0x1385=5540KB/s@[0 -> 2298495]
 Speed Descriptor#0:    02/2298495 R@5.4x1385=7449KB/s W@4.0x1385=5540KB/s
 Speed Descriptor#1:    02/2298495 R@5.4x1385=7449KB/s W@2.0x1385=2770KB/s
READ DVD STRUCTURE[#10h]:
 Media Book Type:       00h, DVD-ROM book [revision 0]
 Legacy lead-out at:    2298496*2KB=4707319808
READ DVD STRUCTURE[#0h]:
 Media Book Type:       33h, DVD-RW book [revision 3]
 Last border-out at:    2045*2KB=4188160
READ DISC INFORMATION:
 Disc status:           appendable
 Number of Sessions:    1
 State of Last Session: incomplete
 "Next" Track:          0
 Number of Tracks:      0
READ FORMAT CAPACITIES:
 unformatted:        2297888*2048=4706074624
 00h(800):        2297888*2048=4706074624
 10h(10):        2297888*2048=4706074624
 15h(10):        2297888*2048=4706074624
READ CAPACITY:          0*2048=0

---

### Post by jjzanti on 2009-09-02
I am running into an error while burning DVDs.  Could anyone tell me what is going on???  The burn seems to work fine but errors everytime.

---

### Post by brynellis on 2009-09-03
I'm glad it's not just me getting this problem!  I've tried on Ubuntu Jaunty, OpenSuse 11.1, Debian and Fedora and can't get DVD iso's to burn.  I can write data to a CD but not DVD.  If I try with Bresaro or Nautilus it just keeps asking me to put in a blank disk, if I try on the command line using growisofs or wodim it never thinks there's anything in the drive either.  I've tried DVD-R and DVD+R none work.  Here's some output from some commands that may help:

_**This is an attempt using wodim:**_
root@victory:/media/BUFFALO2/DownloadsNFS# wodim -sao /dev/dvdrw1 speed=1 Fedora-11-i386-DVD.iso 
Device was not specified. Trying to find an appropriate drive...
Looking for a DVD-R drive to store 3513.17 MiB...
Detected DVD-R drive: /dev/dvdrw
Using /dev/cdrom of unknown capabilities
Device type    : Removable CD-ROM
Version        : 0
Response Format: 2
Capabilities   : 
Vendor_info    : 'SONY    '
Identification : 'DVD RW DRU-510A '
Revision       : '1.1a'
Device seems to be: Generic mmc2 DVD-R/DVD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC-3 SWABAUDIO BURNFREE 
Supported modes: TAO PACKET SAO SAO/R96R RAW/R96R
wodim: No medium found. Cannot open '/dev/dvdrw1'

**_This is the output of lshw -C disk:_**
root@victory:/media/BUFFALO2/DownloadsNFS# lshw -C disk
  *-disk:0                
       description: ATA Disk
       product: Maxtor 6Y080L0
       vendor: Maxtor
       physical id: 0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: YAR4
       serial: Y23F7F4E
       size: 76GiB (81GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=27f927f8
  *-disk:1
       description: ATA Disk
       product: Maxtor 6Y080P0
       vendor: Maxtor
       physical id: 1
       bus info: scsi@3:0.0.0
       logical name: /dev/sdb
       version: YAR4
       serial: Y23N7ADE
       size: 76GiB (81GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=bd59bd59
  *-cdrom
       description: DVD reader
       product: CD-RW  CRX320E
       vendor: SONY
       physical id: 0.1.0
       bus info: scsi@3:0.1.0
       logical name: /dev/cdrom2
       logical name: /dev/cdrw2
       logical name: /dev/dvd2
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: NYK1
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5 status=nodisc
  *-disk
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@6:0.0.0
       logical name: /dev/sdc
       size: 465GiB (500GB)
       capabilities: partitioned partitioned:dos
       configuration: signature=8b711deb
  *-cdrom
       description: DVD writer
       product: DVD RW DRU-510A
       vendor: SONY
       physical id: 0.0.0
       bus info: scsi@7:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrom1
       logical name: /dev/cdrw
       logical name: /dev/cdrw1
       logical name: /dev/dvd
       logical name: /dev/dvd1
       logical name: /dev/dvdrw
       logical name: /dev/dvdrw1
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: 1.1a
       serial: [SONY    DVD RW DRU-510A 1.1a Apr20 ,2004
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: status=nodisc

**_Here's the output from growisofs:_**
root@victory:/media/BUFFALO2/DownloadsNFS# growisofs -speed=2 -dvd-compat -Z /dev/dvdrw=Fedora-11-i386-DVD.iso 
:-( /dev/dvdrw: media is not recognized as recordable DVD: 0

**_Output from uname -a:_**
Linux victory 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686 GNU/Linux

If there's anything else I can run to give more helpful info please let me know.  I'm getting REALLY fed up with this.  I'm a linux fan but Windoze geeks are ridiculing me about this!  I've googled it for about 6 or 7 days now and nobody has a fix.  I find that hard to believe.

Please help.

Thanks in advance.
Bryn

---

### Post by vlats on 2009-12-23
i have similar problem... i can't burn regular CD ( i didnt try burning DVD ) !... ive tried with different burning appications ( K3B, braesero, CD/DVD creator, and one more ive forget its name...

im using laptop lenovo SL 510 with ubuntu 9.1 on it

---

### Post by krekon on 2010-02-26
I have the same Laptop(Lenovo Thinkpad sl 510) and I have the same problem.


We can't burn any cd/dvd


[SIZE="6"]Please help us.[/SIZE]

---

### Post by johnnie69 on 2010-02-26
Same case here burned many different cds/dvds (differends brands) and even bought a new dvd writer. Same problem the old writer produced errors and with K3b produced successful writes with unreadeble media!! With new writer it produces the same thing. Successful write but the media is unmountable/unreadable...

Something is seriously broken in cd/dvd writing in Karmic, it must be kernel or/and wodim issue and a very grave problem. In fact the worst I have ever faced in Ubuntu since 2006 that I am using it and it makes me really sad...

---

### Post by mps_1 on 2010-03-05
I have the same problem with **brasero and K3B**.
The DVD is recorded almost completely but cannot be closed.

The output from Brasero is:

> Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1848)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI no burn:// URI found
BraseroBurnURI stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_set_output_size_for_current_track
BraseroLocalTrack stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack no remote URIs
BraseroLocalTrack stopping
BraseroChecksumFiles called brasero_job_get_output_type
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_set_output_size_for_current_track
BraseroChecksumFiles stopping
BraseroChecksumFiles called brasero_job_get_output_type
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_session_output_size
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_set_current_action
BraseroChecksumFiles called brasero_job_get_flags
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles Adding graft for checksum file /.checksum.md5 file:///tmp/brasero_tmp_313D9U.md5
BraseroChecksumFiles called brasero_job_add_track
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles Finished track successfully
BraseroChecksumFiles stopping
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs getting varg
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs called brasero_job_get_flags
BraseroGrowisofs called brasero_job_get_speed
BraseroGrowisofs called brasero_job_get_device
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_session_output_size
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs called brasero_job_get_fd_in
BraseroGrowisofs Using genisoimage
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs called brasero_job_get_tmp_dir
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs got varg:
	growisofs
	-use-the-force-luke=notray
	-use-the-force-luke=4gms
	-dvd-compat
	-speed=18
	-use-the-force-luke=tty
	-Z
	/dev/sr0
	-dry-run
	-r
	-input-charset
	utf8
	-graft-points
	-D
	-path-list
	/tmp/brasero_tmp_0H8I9U
	-exclude-list
	/tmp/brasero_tmp_6G8I9U
	-print-size
BraseroGrowisofs Launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stdout: Executing 'genisoimage -r -input-charset utf8 -graft-points -D -path-list /tmp/brasero_tmp_0H8I9U -exclude-list /tmp/brasero_tmp_6G8I9U -print-size | builtin_dd of=/dev/sr0 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous

*... here come the files... bla bla bla*

> BraseroGrowisofs called brasero_job_error
BraseroGrowisofs finished with an error
BraseroGrowisofs asked to stop because of an error
	error		= 16
	message	= "No se pudo crear la imagen"
BraseroGrowisofs stopping
BraseroGrowisofs got killed
Session error : No se pudo crear la imagen (brasero_burn_record brasero-burn.c:2808)


---

### Post by jejones3141 on 2010-03-09
Same problem--I'm trying to burn a Karmic Live CD from the .iso file, and I'm seeing the "cannot write medium - incompatible format" error message. Here's the error output from an attempt with k3b.

---

### Post by tava0002 on 2010-03-10
> **johnnie69 said:**
> Same case here burned many different cds/dvds (differends brands) and even bought a new dvd writer. Same problem the old writer produced errors and with K3b produced successful writes with unreadeble media!! With new writer it produces the same thing. Successful write but the media is unmountable/unreadable...

Something is seriously broken in cd/dvd writing in Karmic, it must be kernel or/and wodim issue and a very grave problem. In fact the worst I have ever faced in Ubuntu since 2006 that I am using it and it makes me really sad...

I agree, this is not acceptable I am getting this in the error logs of Brasero and K3b (when it actually recognizes blank media).  It appears to be a known issue that's been around for a while.

BraseroWodim stderr: wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK

I don't know if there's a workaround as far as changing permissions on a certain file, I don't want to install Windows, I might have to try PC-BSD. :(

---

### Post by SaintDanBert on 2010-03-11
> **andrew.46 said:**
> 
...
Perhaps try the burn from the commandline:

```
growisofs -dvd-compat -Z /dev/dvd=*my_distro.iso*
```

changing the name of *my_distro.iso* to the name of your own iso of course :-).
...


[highlight]growisofs[/highlight] worked to burn my distro download.
However, I get errors from both **Brasero** and **K3b**. (I use gnome, but have man KDE parts installed.)
[list]
[*]Brasero doesn't see the DVD-R or DVD+R or DVD-+RW media
[*]K3b doesn't see the media
[*]Brasero complains that it wants plugins without naming which ones
or where to get them
[/list]

Both of these packages worked out-of-box under Ubuntu Hardy (v8.04.3 LTS) and patches.

~~~ 0;-Dan

---

### Post by brynellis on 2010-11-26
Just a quick update on my situation (I know it's been a long time but I've been burning DVD's on Windoze unfortunately).

I've now got a brand spanking new system I built myself with 6 core AMD Phenom II proc etc and running Maverick.  I was hoping the DVD problem would be fixed (not by the new workstation but by Maverick) but sadly the ol' Sony still won't play ball.

So, I bit the bullet and bought this [http://www.ebuyer.com/product/145450]("http://www.ebuyer.com/product/145450") , and I've just burnt my first DVD on Ubuntu!  :D

So, for £15 including delivery I can recommend it.

---

