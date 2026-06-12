---
title: "Jaunty Brasero Issues-Data Burning"
date: 2009-05-10
forum: General Help
---

### Post by joeray on 2009-05-10
I just tried using brasero version 2.26.1 on my new jaunty install. It will allow me to burn a multi-session Data CD, but not a multi-session Data DVD. Is this a function of the type and brand of media disk or a known bug in the software? I have read dozens of forum posts and related google searches and have not found any mention of media incompatibility. I would just like to use a dvd for this pupose for the convenience of data storage size. Is another plugin needed?

---

### Post by Ahunt on 2009-05-11
I think I am experiencing a related problem, so let me describe it here and perhaps someone can address both of them.

I have two PCs, both running Jaunty Ubuntu. The older one has a MITSUMI CR-48X9TE CD-R/CD-RW writer and it works fine with Brasero 2.26.1.

The second PC is a brand new Compaq-Presario with a ATAPI DVD A DH16A6L-C DVD-RAM writer that says "capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram". When using Brasero 2.26.1 it will create CD-RW data discs and ISO images just fine, but it will not create CD-Rs at all. In all cases when a CD-R is run for data or an ISO it runs about half way though burning and then stops, saying "unknown error" and spits out the CD-R. The CD-R has some data on it, but is incomplete and therefore is trash. I have wrecked three CD-Rs so far doing this.

The most recent one I tried was burning an ISO image of Xubuntu 9.04. It worked just fine on a CD-RW and the CD tested fine using the internal test feature on the ISO and worked fine on live session, too. Attempting to burn it on a CD-R resulted in the same error as described above, and another ruined CD-R. The error log showed the following (rather long) error. I can't make out what the problem or the solution is. Is this a software-hardware compatibility problem between Brasero and the ATAPI DVD A DH16A6L-C DVD-RAM writer or something else?

```
Checking session consistency (brasero_burn_check_session_consistency burn.c:1905)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI output set (IMAGE) image = /tmp/brasero_tmp_3ZPZTU.bin toc = none
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI called brasero_job_get_input_type
BraseroBurnURI no burn:// URI found
BraseroBurnURI stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_set_output_size_for_current_track
BraseroLocalTrack stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack output set (IMAGE) image = /tmp/brasero_tmp_S1NZTU.bin toc = none
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
BraseroLocalTrack no remote URIs
BraseroLocalTrack stopping
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_flags
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_set_output_size_for_current_track
BraseroChecksumImage stopping
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_flags
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_session_output_size
BraseroChecksumImage output set (IMAGE) image = /tmp/brasero_tmp_GMMZTU.bin toc = none
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_input_type
BraseroChecksumImage called brasero_job_set_current_action
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage Starting checksuming file /home/ruth/Our Downloads/xubuntu-9.04-desktop-i386.iso (size = 646967296)
BraseroChecksumImage called brasero_job_get_fd_out
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage Setting new checksum (type = 2) 7afaff09c4b192415bad703ee564cff8 ( before)
BraseroChecksumImage Finished track successfully
BraseroChecksumImage stopping
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
	dev=/dev/sr0
	speed=32
	driveropts=burnfree
	-dao
	fs=16m
	-data
	-nopad
	/home/ruth/Our Downloads/xubuntu-9.04-desktop-i386.iso
BraseroWodim Launching command
BraseroWodim called brasero_job_get_fd_out
BraseroWodim stderr: wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/sr0'
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: devname: '/dev/sr0'
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
BraseroWodim stdout: Vendor_info    : 'ATAPI   '
BraseroWodim stdout: Identification : 'DVD A  DH16A6L-C'
BraseroWodim stdout: Revision       : 'ZHCG'
BraseroWodim stdout: Device seems to be: Generic mmc2 DVD-R/DVD-RW.
BraseroWodim stdout: Current: 0x0009 (CD-R)
BraseroWodim stdout: Profile: 0x002B (DVD+R/DL) 
BraseroWodim stdout: Profile: 0x001B (DVD+R) 
BraseroWodim stdout: Profile: 0x001A (DVD+RW) 
BraseroWodim stdout: Profile: 0x0016 (DVD-R/DL layer jump recording) 
BraseroWodim stdout: Profile: 0x0015 (DVD-R/DL sequential recording) 
BraseroWodim stdout: Profile: 0x0014 (DVD-RW sequential recording) 
BraseroWodim stdout: Profile: 0x0013 (DVD-RW restricted overwrite) 
BraseroWodim stdout: Profile: 0x0012 (DVD-RAM) 
BraseroWodim stdout: Profile: 0x0011 (DVD-R sequential recording) 
BraseroWodim stdout: Profile: 0x0010 (DVD-ROM) 
BraseroWodim stdout: Profile: 0x000A (CD-RW) 
BraseroWodim stdout: Profile: 0x0009 (CD-R) (current)
BraseroWodim stdout: Profile: 0x0008 (CD-ROM) 
BraseroWodim stdout: Profile: 0x0002 (Removable disk) 
BraseroWodim stdout: Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
BraseroWodim stdout: Driver flags   : MMC-3 SWABAUDIO BURNFREE FORCESPEED 
BraseroWodim stdout: Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
BraseroWodim stdout: Drive buf size : 1867008 = 1823 KB
BraseroWodim stdout: FIFO size      : 16777216 = 16384 KB
BraseroWodim stderr: Speed set to 5645 KB/s
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Track 01: data   616 MB        
BraseroWodim stdout: Total size:      708 MB (70:12.02) = 315902 sectors
BraseroWodim stdout: Lout start:      708 MB (70:14/02) = 315902 sectors
BraseroWodim stdout: Current Secsize: 2048
BraseroWodim stdout: ATIP info from disk:
BraseroWodim stdout:   Indicated writing power: 5
BraseroWodim stdout:   Is not unrestricted
BraseroWodim stdout:   Is not erasable
BraseroWodim stdout:   Disk sub type: Medium Type B, low Beta category (B-) (4)
BraseroWodim stdout:   ATIP start of lead in:  -11607 (97:27/18)
BraseroWodim stdout:   ATIP start of lead out: 359849 (79:59/74)
BraseroWodim stdout: Disk type:    Short strategy type (Phthalocyanine or similar)
BraseroWodim stdout: Manuf. index: 18
BraseroWodim stdout: Manufacturer: Plasmon Data systems Ltd.
BraseroWodim stdout: Blocks total: 359849 Blocks current: 359849 Blocks remaining: 43947
BraseroWodim stdout: Forcespeed is OFF.
BraseroWodim stdout: Starting to write CD/DVD at speed  32.0 in real SAO mode for single session.
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
BraseroWodim stdout: Waiting for reader process to fill input buffer ... input buffer ready.
BraseroWodim stdout: Performing OPC...
BraseroWodim stdout: Sending CUE sheet...
BraseroWodim called brasero_job_get_input_type
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Writing pregap for track 1 at -150
BraseroWodim stdout: Starting new track at sector: 0
BraseroWodim stdout: 
BraseroWodim stdout: Track 01:    0 of  616 MB written.
BraseroWodim stdout: Track 01:    1 of  616 MB written (fifo 100%) [buf  99%]   0.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    2 of  616 MB written (fifo 100%) [buf 100%]  17.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    3 of  616 MB written (fifo 100%) [buf 100%]  17.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    4 of  616 MB written (fifo  99%) [buf  95%]  16.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    5 of  616 MB written (fifo 100%) [buf 100%]  19.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    6 of  616 MB written (fifo 100%) [buf 100%]  17.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    7 of  616 MB written (fifo 100%) [buf 100%]  18.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    8 of  616 MB written (fifo 100%) [buf 100%]  17.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:    9 of  616 MB written (fifo 100%) [buf 100%]  18.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   10 of  616 MB written (fifo 100%) [buf 100%]  17.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   11 of  616 MB written (fifo 100%) [buf 100%]  18.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   12 of  616 MB written (fifo 100%) [buf 100%]  17.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   13 of  616 MB written (fifo 100%) [buf 100%]  18.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   14 of  616 MB written (fifo 100%) [buf 100%]  17.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   15 of  616 MB written (fifo 100%) [buf 100%]  18.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   16 of  616 MB written (fifo 100%) [buf 100%]  17.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   17 of  616 MB written (fifo 100%) [buf 100%]  18.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   18 of  616 MB written (fifo 100%) [buf 100%]  17.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   19 of  616 MB written (fifo 100%) [buf 100%]  18.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   20 of  616 MB written (fifo 100%) [buf  99%]  18.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   21 of  616 MB written (fifo 100%) [buf 100%]  18.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   22 of  616 MB written (fifo 100%) [buf 100%]  18.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   23 of  616 MB written (fifo 100%) [buf 100%]  18.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   24 of  616 MB written (fifo 100%) [buf 100%]  18.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   25 of  616 MB written (fifo 100%) [buf  86%]  15.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   26 of  616 MB written (fifo 100%) [buf 100%]  21.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   27 of  616 MB written (fifo 100%) [buf 100%]  18.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   28 of  616 MB written (fifo 100%) [buf 100%]  18.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   29 of  616 MB written (fifo 100%) [buf 100%]  18.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   30 of  616 MB written (fifo 100%) [buf 100%]  18.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   31 of  616 MB written (fifo 100%) [buf 100%]  18.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   32 of  616 MB written (fifo 100%) [buf 100%]  18.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   33 of  616 MB written (fifo 100%) [buf 100%]  19.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   34 of  616 MB written (fifo 100%) [buf 100%]  19.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   35 of  616 MB written (fifo 100%) [buf 100%]  19.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   36 of  616 MB written (fifo 100%) [buf 100%]  19.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   37 of  616 MB written (fifo 100%) [buf 100%]  19.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   38 of  616 MB written (fifo 100%) [buf 100%]  19.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   39 of  616 MB written (fifo 100%) [buf 100%]  19.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   40 of  616 MB written (fifo 100%) [buf 100%]  19.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   41 of  616 MB written (fifo 100%) [buf 100%]  19.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   42 of  616 MB written (fifo 100%) [buf 100%]  19.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   43 of  616 MB written (fifo 100%) [buf 100%]  19.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   44 of  616 MB written (fifo 100%) [buf 100%]  19.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   45 of  616 MB written (fifo 100%) [buf 100%]  19.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   46 of  616 MB written (fifo 100%) [buf 100%]  20.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   47 of  616 MB written (fifo 100%) [buf 100%]  19.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   48 of  616 MB written (fifo 100%) [buf 100%]  20.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   49 of  616 MB written (fifo 100%) [buf 100%]  19.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   50 of  616 MB written (fifo 100%) [buf 100%]  20.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   51 of  616 MB written (fifo 100%) [buf 100%]  19.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   52 of  616 MB written (fifo 100%) [buf 100%]  20.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   53 of  616 MB written (fifo 100%) [buf 100%]  19.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   54 of  616 MB written (fifo 100%) [buf 100%]  20.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   55 of  616 MB written (fifo 100%) [buf 100%]  19.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   56 of  616 MB written (fifo 100%) [buf 100%]  20.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   57 of  616 MB written (fifo 100%) [buf 100%]  19.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   58 of  616 MB written (fifo 100%) [buf 100%]  20.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   59 of  616 MB written (fifo 100%) [buf 100%]  19.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   60 of  616 MB written (fifo 100%) [buf 100%]  20.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   61 of  616 MB written (fifo 100%) [buf 100%]  19.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   62 of  616 MB written (fifo 100%) [buf 100%]  20.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   63 of  616 MB written (fifo 100%) [buf 100%]  19.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   64 of  616 MB written (fifo 100%) [buf 100%]  20.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   65 of  616 MB written (fifo 100%) [buf 100%]  21.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   66 of  616 MB written (fifo 100%) [buf 100%]  20.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   67 of  616 MB written (fifo 100%) [buf 100%]  21.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   68 of  616 MB written (fifo 100%) [buf 100%]  20.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   69 of  616 MB written (fifo 100%) [buf 100%]  21.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   70 of  616 MB written (fifo 100%) [buf 100%]  20.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   71 of  616 MB written (fifo  99%) [buf  85%]  17.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   72 of  616 MB written (fifo  99%) [buf  22%]  11.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   73 of  616 MB written (fifo 100%) [buf  89%] 195.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   74 of  616 MB written (fifo 100%) [buf 100%]  23.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   75 of  616 MB written (fifo 100%) [buf 100%]  21.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   76 of  616 MB written (fifo 100%) [buf 100%]  20.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   77 of  616 MB written (fifo 100%) [buf 100%]  21.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   78 of  616 MB written (fifo 100%) [buf 100%]  20.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   79 of  616 MB written (fifo 100%) [buf 100%]  21.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   80 of  616 MB written (fifo 100%) [buf 100%]  20.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   81 of  616 MB written (fifo 100%) [buf 100%]  21.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   82 of  616 MB written (fifo 100%) [buf 100%]  20.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   83 of  616 MB written (fifo 100%) [buf 100%]  21.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   84 of  616 MB written (fifo 100%) [buf 100%]  21.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   85 of  616 MB written (fifo 100%) [buf 100%]  21.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   86 of  616 MB written (fifo 100%) [buf 100%]  21.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   87 of  616 MB written (fifo 100%) [buf 100%]  21.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   88 of  616 MB written (fifo 100%) [buf 100%]  21.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   89 of  616 MB written (fifo 100%) [buf 100%]  21.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   90 of  616 MB written (fifo 100%) [buf 100%]  21.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   91 of  616 MB written (fifo 100%) [buf 100%]  21.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   92 of  616 MB written (fifo 100%) [buf 100%]  21.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   93 of  616 MB written (fifo 100%) [buf 100%]  21.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   94 of  616 MB written (fifo 100%) [buf 100%]  21.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   95 of  616 MB written (fifo 100%) [buf 100%]  21.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   96 of  616 MB written (fifo 100%) [buf  88%]  19.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   97 of  616 MB written (fifo 100%) [buf 100%]  25.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   98 of  616 MB written (fifo 100%) [buf 100%]  22.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:   99 of  616 MB written (fifo 100%) [buf 100%]  21.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  100 of  616 MB written (fifo  99%) [buf 100%]  22.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  101 of  616 MB written (fifo 100%) [buf 100%]  22.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  102 of  616 MB written (fifo 100%) [buf 100%]  22.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  103 of  616 MB written (fifo 100%) [buf 100%]  22.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  104 of  616 MB written (fifo 100%) [buf 100%]  22.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  105 of  616 MB written (fifo  99%) [buf 100%]  22.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  106 of  616 MB written (fifo 100%) [buf 100%]  22.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  107 of  616 MB written (fifo 100%) [buf 100%]  22.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  108 of  616 MB written (fifo 100%) [buf 100%]  22.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  109 of  616 MB written (fifo 100%) [buf 100%]  22.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  110 of  616 MB written (fifo 100%) [buf 100%]  22.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  111 of  616 MB written (fifo 100%) [buf 100%]  22.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  112 of  616 MB written (fifo 100%) [buf 100%]  22.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  113 of  616 MB written (fifo 100%) [buf 100%]  22.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  114 of  616 MB written (fifo 100%) [buf 100%]  23.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  115 of  616 MB written (fifo 100%) [buf 100%]  22.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  116 of  616 MB written (fifo 100%) [buf 100%]  23.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  117 of  616 MB written (fifo 100%) [buf 100%]  22.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  118 of  616 MB written (fifo 100%) [buf 100%]  23.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  119 of  616 MB written (fifo 100%) [buf 100%]  22.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  120 of  616 MB written (fifo 100%) [buf  97%]  22.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  121 of  616 MB written (fifo 100%) [buf 100%]  23.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  122 of  616 MB written (fifo 100%) [buf 100%]  23.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  123 of  616 MB written (fifo 100%) [buf 100%]  22.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  124 of  616 MB written (fifo 100%) [buf 100%]  23.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  125 of  616 MB written (fifo 100%) [buf 100%]  22.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  126 of  616 MB written (fifo 100%) [buf 100%]  23.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  127 of  616 MB written (fifo 100%) [buf 100%]  23.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  128 of  616 MB written (fifo  99%) [buf 100%]  23.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  129 of  616 MB written (fifo 100%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  130 of  616 MB written (fifo 100%) [buf 100%]  23.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  131 of  616 MB written (fifo 100%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  132 of  616 MB written (fifo 100%) [buf 100%]  23.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  133 of  616 MB written (fifo 100%) [buf 100%]  24.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  134 of  616 MB written (fifo 100%) [buf 100%]  23.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  135 of  616 MB written (fifo 100%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  136 of  616 MB written (fifo 100%) [buf 100%]  23.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  137 of  616 MB written (fifo 100%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  138 of  616 MB written (fifo 100%) [buf 100%]  23.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  139 of  616 MB written (fifo 100%) [buf 100%]  24.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  140 of  616 MB written (fifo  99%) [buf 100%]  23.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  141 of  616 MB written (fifo 100%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  142 of  616 MB written (fifo 100%) [buf 100%]  23.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  143 of  616 MB written (fifo 100%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  144 of  616 MB written (fifo 100%) [buf 100%]  23.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  145 of  616 MB written (fifo 100%) [buf 100%]  24.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  146 of  616 MB written (fifo 100%) [buf 100%]  23.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  147 of  616 MB written (fifo 100%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  148 of  616 MB written (fifo 100%) [buf 100%]  23.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  149 of  616 MB written (fifo 100%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  150 of  616 MB written (fifo 100%) [buf 100%]  23.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  151 of  616 MB written (fifo 100%) [buf 100%]  24.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  152 of  616 MB written (fifo 100%) [buf 100%]  23.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  153 of  616 MB written (fifo 100%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  154 of  616 MB written (fifo  99%) [buf 100%]  23.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  155 of  616 MB written (fifo 100%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  156 of  616 MB written (fifo 100%) [buf 100%]  23.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  157 of  616 MB written (fifo 100%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  158 of  616 MB written (fifo  99%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  159 of  616 MB written (fifo 100%) [buf 100%]  24.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  160 of  616 MB written (fifo 100%) [buf 100%]  25.2x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  161 of  616 MB written (fifo 100%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  162 of  616 MB written (fifo 100%) [buf 100%]  25.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  163 of  616 MB written (fifo 100%) [buf 100%]  24.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  164 of  616 MB written (fifo  99%) [buf  99%]  25.1x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  165 of  616 MB written (fifo 100%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  166 of  616 MB written (fifo 100%) [buf 100%]  25.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  167 of  616 MB written (fifo 100%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  168 of  616 MB written (fifo 100%) [buf 100%]  25.3x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  169 of  616 MB written (fifo 100%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  170 of  616 MB written (fifo 100%) [buf 100%]  25.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  171 of  616 MB written (fifo 100%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  172 of  616 MB written (fifo 100%) [buf 100%]  25.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  173 of  616 MB written (fifo 100%) [buf 100%]  24.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  174 of  616 MB written (fifo  99%) [buf 100%]  25.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  175 of  616 MB written (fifo 100%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  176 of  616 MB written (fifo 100%) [buf 100%]  25.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  177 of  616 MB written (fifo  99%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  178 of  616 MB written (fifo 100%) [buf 100%]  25.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  179 of  616 MB written (fifo 100%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  180 of  616 MB written (fifo  99%) [buf 100%]  25.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  181 of  616 MB written (fifo 100%) [buf 100%]  24.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  182 of  616 MB written (fifo 100%) [buf 100%]  25.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  183 of  616 MB written (fifo 100%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  184 of  616 MB written (fifo  99%) [buf 100%]  25.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  185 of  616 MB written (fifo  99%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  186 of  616 MB written (fifo 100%) [buf 100%]  25.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  187 of  616 MB written (fifo 100%) [buf 100%]  24.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  188 of  616 MB written (fifo 100%) [buf 100%]  25.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  189 of  616 MB written (fifo 100%) [buf 100%]  26.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  190 of  616 MB written (fifo 100%) [buf 100%]  25.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  191 of  616 MB written (fifo 100%) [buf 100%]  26.4x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  192 of  616 MB written (fifo 100%) [buf 100%]  25.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  193 of  616 MB written (fifo 100%) [buf 100%]  26.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  194 of  616 MB written (fifo 100%) [buf 100%]  25.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  195 of  616 MB written (fifo 100%) [buf 100%]  26.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  196 of  616 MB written (fifo 100%) [buf 100%]  25.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  197 of  616 MB written (fifo 100%) [buf 100%]  26.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  198 of  616 MB written (fifo 100%) [buf 100%]  25.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  199 of  616 MB written (fifo 100%) [buf 100%]  26.5x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  200 of  616 MB written (fifo 100%) [buf 100%]  25.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  201 of  616 MB written (fifo 100%) [buf 100%]  26.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  202 of  616 MB written (fifo  99%) [buf 100%]  25.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  203 of  616 MB written (fifo  99%) [buf 100%]  26.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  204 of  616 MB written (fifo 100%) [buf 100%]  25.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  205 of  616 MB written (fifo 100%) [buf 100%]  26.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  206 of  616 MB written (fifo 100%) [buf 100%]  25.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  207 of  616 MB written (fifo  99%) [buf 100%]  26.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  208 of  616 MB written (fifo 100%) [buf 100%]  25.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  209 of  616 MB written (fifo 100%) [buf 100%]  26.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  210 of  616 MB written (fifo  99%) [buf 100%]  25.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  211 of  616 MB written (fifo 100%) [buf 100%]  26.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  212 of  616 MB written (fifo 100%) [buf 100%]  25.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  213 of  616 MB written (fifo 100%) [buf 100%]  26.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  214 of  616 MB written (fifo 100%) [buf 100%]  25.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  215 of  616 MB written (fifo 100%) [buf 100%]  26.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  216 of  616 MB written (fifo  99%) [buf 100%]  25.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  217 of  616 MB written (fifo 100%) [buf 100%]  26.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  218 of  616 MB written (fifo  99%) [buf 100%]  25.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  219 of  616 MB written (fifo 100%) [buf 100%]  26.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  220 of  616 MB written (fifo 100%) [buf 100%]  27.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  221 of  616 MB written (fifo 100%) [buf 100%]  26.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  222 of  616 MB written (fifo 100%) [buf 100%]  27.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  223 of  616 MB written (fifo 100%) [buf 100%]  26.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  224 of  616 MB written (fifo  99%) [buf 100%]  27.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  225 of  616 MB written (fifo 100%) [buf 100%]  26.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  226 of  616 MB written (fifo  99%) [buf 100%]  27.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  227 of  616 MB written (fifo 100%) [buf 100%]  26.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  228 of  616 MB written (fifo 100%) [buf 100%]  27.6x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  229 of  616 MB written (fifo  99%) [buf 100%]  26.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  230 of  616 MB written (fifo 100%) [buf 100%]  27.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  231 of  616 MB written (fifo 100%) [buf 100%]  26.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  232 of  616 MB written (fifo  99%) [buf 100%]  27.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  233 of  616 MB written (fifo 100%) [buf 100%]  26.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  234 of  616 MB written (fifo 100%) [buf 100%]  27.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  235 of  616 MB written (fifo 100%) [buf 100%]  26.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  236 of  616 MB written (fifo  99%) [buf 100%]  27.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  237 of  616 MB written (fifo 100%) [buf 100%]  26.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  238 of  616 MB written (fifo 100%) [buf 100%]  27.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  239 of  616 MB written (fifo 100%) [buf 100%]  26.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  240 of  616 MB written (fifo  99%) [buf 100%]  27.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  241 of  616 MB written (fifo  99%) [buf 100%]  26.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  242 of  616 MB written (fifo 100%) [buf 100%]  27.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  243 of  616 MB written (fifo 100%) [buf 100%]  26.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  244 of  616 MB written (fifo 100%) [buf 100%]  27.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  245 of  616 MB written (fifo 100%) [buf 100%]  26.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  246 of  616 MB written (fifo 100%) [buf 100%]  27.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  247 of  616 MB written (fifo 100%) [buf 100%]  27.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  248 of  616 MB written (fifo  99%) [buf 100%]  27.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  249 of  616 MB written (fifo  99%) [buf 100%]  27.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  250 of  616 MB written (fifo 100%) [buf 100%]  27.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  251 of  616 MB written (fifo  99%) [buf 100%]  28.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  252 of  616 MB written (fifo 100%) [buf 100%]  27.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  253 of  616 MB written (fifo  99%) [buf 100%]  28.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  254 of  616 MB written (fifo 100%) [buf 100%]  27.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  255 of  616 MB written (fifo 100%) [buf 100%]  28.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  256 of  616 MB written (fifo 100%) [buf 100%]  27.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  257 of  616 MB written (fifo 100%) [buf 100%]  28.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  258 of  616 MB written (fifo 100%) [buf 100%]  27.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  259 of  616 MB written (fifo 100%) [buf 100%]  28.7x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  260 of  616 MB written (fifo 100%) [buf 100%]  27.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  261 of  616 MB written (fifo 100%) [buf 100%]  28.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  262 of  616 MB written (fifo  99%) [buf 100%]  27.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  263 of  616 MB written (fifo  99%) [buf 100%]  28.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  264 of  616 MB written (fifo 100%) [buf 100%]  27.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  265 of  616 MB written (fifo 100%) [buf 100%]  28.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  266 of  616 MB written (fifo 100%) [buf 100%]  27.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  267 of  616 MB written (fifo 100%) [buf 100%]  28.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  268 of  616 MB written (fifo 100%) [buf  99%]  27.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  269 of  616 MB written (fifo 100%) [buf 100%]  28.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  270 of  616 MB written (fifo 100%) [buf 100%]  27.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  271 of  616 MB written (fifo  99%) [buf  99%]  28.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  272 of  616 MB written (fifo 100%) [buf 100%]  27.9x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Track 01:  273 of  616 MB written (fifo 100%) [buf 100%]  28.8x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stderr: Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: CDB:  2A 00 00 02 24 6F 00 00 1F 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: status: 0x2 (CHECK CONDITION)
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Bytes: 71 00 03 00 00 00 00 0A 00 00 00 00 0C 00 00 00
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Key: 0x3 Medium Error, deferred error, Segment 0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense Code: 0x0C Qual 0x00 (write error) Fru 0x0
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: Sense flags: Blk 0 (not valid) 
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: cmd finished after 29.178s timeout 200s
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: A write error occured.
BraseroWodim called brasero_job_get_flags
BraseroWodim stderr: wodim: Please properly read the error message above.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: Track 01:  274 of  616 MB written (fifo  99%) [buf 100%]  28.0x.
BraseroWodim called brasero_job_get_action
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: write track data: error after 287537152 bytes
BraseroWodim stdout: Writing  time:  135.688s
BraseroWodim stdout: Average write speed  32.7x.
BraseroWodim stdout: Min drive buffer fill was 22%
BraseroWodim stdout: Fixating...
BraseroWodim called brasero_job_set_current_action
BraseroWodim stdout: Fixating time:    0.002s
BraseroWodim stderr: wodim: fifo had 4784 puts and 4530 gets.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: BURN-Free was 1 times used.
BraseroWodim stderr: wodim: fifo was 0 times empty and 3969 times full, min fill was 95%.
BraseroWodim called brasero_job_get_flags
BraseroWodim stdout: HUP
BraseroWodim stderr: HUP
BraseroWodim process finished with status 254
BraseroWodim called brasero_job_error
BraseroWodim finished with an error
BraseroWodim asked to stop because of an error
	error		= 0
	message	= "no message"
BraseroWodim stopping
BraseroWodim got killed
Session error : unknown (brasero_burn_record burn.c:2602)
```

---

### Post by Ahunt on 2009-05-11
Incidentally I had a look through Launchpad and while there are a number of outstanding bugs on Brasero nothing seems to match the two mentioned here:

[https://bugs.launchpad.net/ubuntu/+bugs?field.searchtext=Brasero&orderby=-datecreated&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=](https://bugs.launchpad.net/ubuntu/+bugs?field.searchtext=Brasero&orderby=-datecreated&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=)

---

### Post by Ahunt on 2009-05-12
Also had a look through the Gnome BugZilla list of outstanding bugs at [http://bugzilla.gnome.org/buglist.cgi?query=Brasero](http://bugzilla.gnome.org/buglist.cgi?query=Brasero) and didn't see anything similar to these reported problems.

Does anyone else have any suggestions on these issues?

---

### Post by joeray on 2009-05-13
Well, I tried to get support for my issue with brasero. No Luck! I installed K3B. I will reinstall brasero when debugged. Just to let all know the newest version package downloaded from the regular repositories works like a charm for my purpose of burning backup data multisession dvd's. Easy to navigate and understand giu. Try it if you are experiencing and multisession problems with brasero.

P. S. Ahunt, nice kitty, joeray out.

---

### Post by Ahunt on 2009-05-14
joeray:

Thanks for the info on your experiences with K3B! I will give it a try and report back here.

I assume that since [155 people read it]("http://ubuntuforums.org/search.php?searchid=59403119") that no one had encountered the problem or they didn't have an answer to it.

---

### Post by Ahunt on 2009-05-14
Well this is interesting. I installed K3B and it is a good application, easy to use and works well. I did some testing on CD-RWs and it recorded fine on the PC with the ATAPI DVD A DH16A6L-C DVD-RAM writer.

I tried writing to a CD-R and the ATAPI DVD A DH16A6L-C DVD-RAM writer didn't recognize that the CD was in the drive and neither did Ubuntu's Nautilus file system. 

I tried the CD-R in my other PC and it failed to recognize the CD-R as well. It seems it was a bad CD. This was a generic-brand CD-R, so I tried making a CD-R of a Ubuntu ISO using a brand-name Philips CD-R in the ATAPI DVD A DH16A6L-C DVD-RAM writer with K3B and it wrote to it just fine and the CD tested correctly using the built-in ISO test.

Next I tried making a CD of a Ubuntu ISO using Brasero and the ATAPI DVD A DH16A6L-C DVD-RAM writer and a Philips CD-R and it worked fine, too.

I can only conclude that the problem encountered was not Brasero but the no-name brand CD-Rs. Strangely enough these worked fine on my other PC with the older MITSUMI CR-48X9TE CD-R/CD-RW writer, but perhaps the newer ATAPI DVD A DH16A6L-C hardware, being a combination DVD and CD writer is more sensitive to these no-name brand CDs?

Regardless I believe that this problem is solved.

---

### Post by joeray on 2009-05-14
Ahunt,
I'm glad to see your problem is solved by changing media brands. I didn't try that during my troubleshooting because the disk was recognized to burn to as a regular data burning session in brasero, but not as a multisession. The option to do so was greyed out. This problem was unique to dvd burning and not a problem when burning a cd. I still think this is a bug in the software code. I'm very satisfied with K3b and would be hard pressed now to change. Best of Luck and Happy Burning!

---

### Post by joeray on 2009-05-20
> **joeray said:**
> I just tried using brasero version 2.26.1 on my new jaunty install. It will allow me to burn a multi-session Data CD, but not a multi-session Data DVD. Is this a function of the type and brand of media disk or a known bug in the software? I have read dozens of forum posts and related google searches and have not found any mention of media incompatibility. I would just like to use a dvd for this pupose for the convenience of data storage size. Is another plugin needed?

):P I'd like to let the community know, that I gave brasero another try this morning after downloading the version that is in the repositories now. I tried burning multisession dvd's and cd's with the same brand media disks that I was using when I had problems before. All burning projects went smoothly. Unbuntu is reading the data disk without any problems. This bug seems to be gone from brasero.
Joeray out! FREEDOM ISN'T FREE.

Compaq Presario RZ537AA-ABA SR5010NX
Intel Integrated 945 Chipset, 1.5GB Ram
Intel(R) Celeron(R) D CPU 3.46GHz
Jaunty 9.04 2.6.28-11 Generic Kernel
Gnome 2.26.1

---

