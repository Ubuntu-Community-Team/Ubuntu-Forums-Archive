---
title: "Problems burning a DVD under Ubuntu 9.04 Jaunty"
date: 2009-05-30
forum: Desktop Environments
---

### Post by drkameleon on 2009-05-30
Hi guys!

I've been trying to write some data or a DVD .iso to a blank DVD+R (RW) under Ubuntu 9.04 Jaunty, using Brasero, K3B and GnomeBaker and I seem to be having some problem...

I tried decreasing the speed (@ 2.4x) but it didn't help.

Brasero crashes giving the following error log :

```
Checking session consistency (brasero_burn_check_session_consistency burn.c:1905)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI called brasero_job_get_input_type
BraseroBurnURI burn:// URI found burn:///house.of.sand.and.fog.(2003).eng.1cd.(3113678).zip.part
BraseroBurnURI called brasero_job_set_current_action
BraseroBurnURI called brasero_job_get_current_track
BraseroBurnURI Information retrieval for burn:///house.of.sand.and.fog.(2003).eng.1cd.(3113678).zip.part
BraseroBurnURI Added file /home/drkameleon/Desktop/house.of.sand.and.fog.(2003).eng.1cd.(3113678).zip.part at /house.of.sand.and.fog.(2003).eng.1cd.(3113678).zip.part
BraseroBurnURI Information retrieval for burn:///house.of.sand.and.fog.(2003).eng.1cd.(3113678)(3).zip
BraseroBurnURI Added file /home/drkameleon/Desktop/house.of.sand.and.fog.(2003).eng.1cd.(3113678)(3).zip at /house.of.sand.and.fog.(2003).eng.1cd.(3113678)(3).zip
BraseroBurnURI Information retrieval for burn:///house.of.sand.and.fog.(2003).eng.1cd.(3113678)(2).zip.part
BraseroBurnURI Added file /home/drkameleon/Desktop/house.of.sand.and.fog.(2003).eng.1cd.(3113678)(2).zip.part at /house.of.sand.and.fog.(2003).eng.1cd.(3113678)(2).zip.part
BraseroBurnURI called brasero_job_add_track
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI Finished track successfully
BraseroBurnURI stopping
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
BraseroChecksumFiles called brasero_job_get_input_type
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_set_current_action
BraseroChecksumFiles called brasero_job_get_flags
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_input_type
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles Adding graft for checksum file /.checksum.md5 file:///tmp/brasero_tmp_O685UU.md5
BraseroChecksumFiles called brasero_job_add_track
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles Finished track successfully
BraseroChecksumFiles stopping
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs getting varg
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_input_type
BraseroGrowisofs called brasero_job_get_flags
BraseroGrowisofs called brasero_job_get_speed
BraseroGrowisofs called brasero_job_get_device
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_session_output_size
BraseroGrowisofs called brasero_job_get_input_type
BraseroGrowisofs called brasero_job_get_fd_in
BraseroGrowisofs Using genisoimage
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs called brasero_job_get_input_type
BraseroGrowisofs called brasero_job_get_tmp_dir
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs got varg:
	growisofs
	-use-the-force-luke=notray
	-use-the-force-luke=4gms
	-dvd-compat
	-speed=2
	-use-the-force-luke=tty
	-Z
	/dev/sr0
	-dry-run
	-r
	-J
	-input-charset
	utf8
	-graft-points
	-path-list
	/tmp/brasero_tmp_8825UU
	-exclude-list
	/tmp/brasero_tmp_C725UU
	-print-size
BraseroGrowisofs Launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stderr: Using HOUSE000.PAR;1 for  /house.of.sand.and.fog.(2003).eng.1cd.(3113678)(2).zip.part (house.of.sand.and.fog.(2003).eng.1cd.(3113678).zip.part)
BraseroGrowisofs stdout: Executing 'genisoimage -r -J -input-charset utf8 -graft-points -path-list /tmp/brasero_tmp_8825UU -exclude-list /tmp/brasero_tmp_C725UU -print-size | builtin_dd of=/dev/sr0 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous
BraseroGrowisofs stderr: Total extents scheduled to be written = 219
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_output_size_for_current_track
BraseroGrowisofs Finished successfully session
BraseroGrowisofs stopping
BraseroGrowisofs got killed
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs getting varg
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_flags
BraseroGrowisofs called brasero_job_get_speed
BraseroGrowisofs called brasero_job_get_device
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_session_output_size
BraseroGrowisofs called brasero_job_get_input_type
BraseroGrowisofs called brasero_job_get_fd_in
BraseroGrowisofs Using genisoimage
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs called brasero_job_get_input_type
BraseroGrowisofs called brasero_job_get_tmp_dir
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_data_label
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs got varg:
	growisofs
	-use-the-force-luke=notray
	-use-the-force-luke=4gms
	-dvd-compat
	-speed=2
	-use-the-force-luke=tracksize:219
	-use-the-force-luke=tty
	-Z
	/dev/sr0
	-r
	-J
	-input-charset
	utf8
	-graft-points
	-path-list
	/tmp/brasero_tmp_O2JBVU
	-exclude-list
	/tmp/brasero_tmp_T0JBVU
	-V
	Data disc (31 May 09)
	-A
	Brasero-2.26.1
	-sysid
	LINUX
	-v
BraseroGrowisofs Launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stderr: genisoimage 1.1.9 (Linux)
BraseroGrowisofs stdout: Executing 'genisoimage -r -J -input-charset utf8 -graft-points -path-list /tmp/brasero_tmp_O2JBVU -exclude-list /tmp/brasero_tmp_T0JBVU -V Data disc (31 May 09) -A Brasero-2.26.1 -sysid LINUX -v | builtin_dd of=/dev/sr0 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous
BraseroGrowisofs stderr: Using HOUSE000.PAR;1 for  /house.of.sand.and.fog.(2003).eng.1cd.(3113678)(2).zip.part (house.of.sand.and.fog.(2003).eng.1cd.(3113678).zip.part)
BraseroGrowisofs stderr: Writing:   Initial Padblock                        Start Block 0
BraseroGrowisofs stderr: Done with: Initial Padblock                        Block(s)    16
BraseroGrowisofs stderr: Writing:   Primary Volume Descriptor               Start Block 16
BraseroGrowisofs stderr: Done with: Primary Volume Descriptor               Block(s)    1
BraseroGrowisofs stderr: Writing:   Joliet Volume Descriptor                Start Block 17
BraseroGrowisofs stderr: Done with: Joliet Volume Descriptor                Block(s)    1
BraseroGrowisofs stderr: Writing:   End Volume Descriptor                   Start Block 18
BraseroGrowisofs stderr: Done with: End Volume Descriptor                   Block(s)    1
BraseroGrowisofs stderr: Writing:   Version block                           Start Block 19
BraseroGrowisofs stderr: Done with: Version block                           Block(s)    1
BraseroGrowisofs stderr: Writing:   Path table                              Start Block 20
BraseroGrowisofs stderr: Done with: Path table                              Block(s)    4
BraseroGrowisofs stderr: Writing:   Joliet path table                       Start Block 24
BraseroGrowisofs stderr: Done with: Joliet path table                       Block(s)    4
BraseroGrowisofs stderr: Writing:   Directory tree                          Start Block 28
BraseroGrowisofs stderr: Done with: Directory tree                          Block(s)    1
BraseroGrowisofs stderr: Writing:   Joliet directory tree                   Start Block 29
BraseroGrowisofs stderr: Done with: Joliet directory tree                   Block(s)    1
BraseroGrowisofs stderr: Writing:   Directory tree cleanup                  Start Block 30
BraseroGrowisofs stderr: Done with: Directory tree cleanup                  Block(s)    0
BraseroGrowisofs stderr: Writing:   Extension record                        Start Block 30
BraseroGrowisofs stderr: Done with: Extension record                        Block(s)    1
BraseroGrowisofs stderr: Writing:   The File(s)                             Start Block 31
BraseroGrowisofs stderr: Total translation table size: 0
BraseroGrowisofs stderr: Total rockridge attributes bytes: 636
BraseroGrowisofs stderr: Total directory bytes: 0
BraseroGrowisofs stderr: Path table size(bytes): 10
BraseroGrowisofs stderr: Done with: The File(s)                             Block(s)    38
BraseroGrowisofs stderr: Writing:   Ending Padblock                         Start Block 69
BraseroGrowisofs stderr: Done with: Ending Padblock                         Block(s)    150
BraseroGrowisofs stderr: Max brk space used 0
BraseroGrowisofs stderr: 219 extents written (0 MB)
BraseroGrowisofs stderr: /dev/sr0: "Current Write Speed" is 2.5x1352KBps.
BraseroGrowisofs stderr: :-[ WRITE@LBA=0h failed with SK=3h/POWER CALIBRATION AREA ERROR]: Input/output error
BraseroGrowisofs stderr: :-( write failed: Input/output error
BraseroGrowisofs stderr: HUP
BraseroGrowisofs stdout: HUP
BraseroGrowisofs process finished with status 5
BraseroGrowisofs called brasero_job_error
BraseroGrowisofs finished with an error
BraseroGrowisofs asked to stop because of an error
	error		= 0
	message	= "no message"
BraseroGrowisofs stopping
BraseroGrowisofs got killed
Session error : unknown (brasero_burn_record burn.c:2602)

```

Do you have any idea why this is happening?

**I MUST solve this one ASAP.**

Thanks in advance!

Dr.Kameleon

---

### Post by drkameleon on 2009-05-30
Btw, I should also mention that I have absolutely NO hardware problems - as I have been able to write CDs & DVDs flawlessly in the past running either OLDER Ubuntu Releases or Windows...:(

---

### Post by drkameleon on 2009-06-12
Up ^

---

### Post by gradinaruvasile on 2009-06-12
Try
[http://www.nero.com/eng/downloads-linux3-trial.php]("http://www.nero.com/eng/downloads-linux3-trial.php")
Or reinstall brasero to a previous version maybe?

---

### Post by drkameleon on 2009-06-12
> **gradinaruvasile said:**
> Try
[http://www.nero.com/eng/downloads-linux3-trial.php]("http://www.nero.com/eng/downloads-linux3-trial.php")
Or reinstall brasero to a previous version maybe?

You again? LOL :p

I suppose after all this, one of my issues - either the DVD Burning or the Sound, will be resolved in the end...

;)

---

### Post by drkameleon on 2009-06-12
I've downloaded and installed the Linux-version of Nero (I think I'd already done this in the past) but - ALTHOUGH writting CDs works just fine - whenever I try to burn some DVD, it crashes...:(

Perhaps, the issue seems quite deeper and not app-related. Do you still think a downgrade would help that much? (i have no idea how i could downgrade it, btw)

Thanks!

---

### Post by gradinaruvasile on 2009-06-12
Are u using the default versions of these programs?
What are you trying to write on the DVD? It seems to be a long filename... Maybe you try shortening the file name and removing points and such...
Look at this (the same error you had):
[http://ubuntuforums.org/showthread.php?t=1141272&page=2]("http://ubuntuforums.org/showthread.php?t=1141272&page=2")

---

### Post by drkameleon on 2009-06-12
Nope. There are NO long filenames, and I've already tried every single program (Brasero, Gnomebaker, K3b, Nero...), I've "played" with the writing speed and I've also tried different media (+R, -R, -RW, different brands, etc)

**The main ERROR is :**

```
failed with SK=3h/POWER CALIBRATION AREA ERROR
```

Does anybody have any idea on how this could be fixed???:confused:

---

### Post by hibliss on 2009-06-12
Calibration area error is generally an issue with the drive not liking the discs. Some of the cheaper discs cause this issue. I have had the same error on my Plextor with Memorex discs, and another brand I cannot think of off the top of my head.

Also note that the discs that did not work in my burner worked fine in my wife's notebook.

Try getting a single disc at the store, a high end disc. If that solves the problem, you know for certain it is the discs.

Even if you have had success on the same spindle, it means nothing if you are repeatedly getting this error.

---

