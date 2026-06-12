---
title: "cant burn any thing on cd or dvd"
date: 2009-06-18
forum: General Help
---

### Post by hero1900 on 2009-06-18
i have this problem i cant burn any data or images on any media (cd or dvd) i try both brasero and k3b. it give me error before beginning the burning process 
here is log file contain the error:

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
BraseroLocalTrack called brasero_job_get_input_type
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
BraseroChecksumFiles called brasero_job_get_input_type
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_set_current_action
BraseroChecksumFiles called brasero_job_get_flags
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_input_type
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles Adding graft for checksum file /.checksum.md5 file:///tmp/brasero_tmp_E9TMVU.md5
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
    -speed=8
    -use-the-force-luke=tty
    -Z
    /dev/sr0
    -dry-run
    -r
    -iso-level
    3
    -allow-limited-size
    -udf
    -input-charset
    utf8
    -graft-points
    -path-list
    /tmp/brasero_tmp_JF9WVU
    -exclude-list
    /tmp/brasero_tmp_D0DUVU
    -print-size
BraseroGrowisofs Launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stdout: Executing 'genisoimage -r -iso-level 3 -allow-limited-size -udf -input-charset utf8 -graft-points -path-list /tmp/brasero_tmp_JF9WVU -exclude-list /tmp/brasero_tmp_D0DUVU -print-size | builtin_dd of=/dev/sr0 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous
BraseroGrowisofs stderr: Total extents scheduled to be written = 1596562
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
    -speed=8
    -use-the-force-luke=tracksize:1596562
    -use-the-force-luke=tty
    -Z
    /dev/sr0
    -r
    -iso-level
    3
    -allow-limited-size
    -udf
    -input-charset
    utf8
    -graft-points
    -path-list
    /tmp/brasero_tmp_RWLQVU
    -exclude-list
    /tmp/brasero_tmp_2ULQVU
    -V
    Data disc (18 Jun 09)
    -A
    Brasero-2.26.1
    -sysid
    LINUX
    -v
BraseroGrowisofs Launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stderr: genisoimage 1.1.9 (Linux)
BraseroGrowisofs stdout: Executing 'genisoimage -r -iso-level 3 -allow-limited-size -udf -input-charset utf8 -graft-points -path-list /tmp/brasero_tmp_RWLQVU -exclude-list /tmp/brasero_tmp_2ULQVU -V Data disc (18 Jun 09) -A Brasero-2.26.1 -sysid LINUX -v | builtin_dd of=/dev/sr0 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous
BraseroGrowisofs stderr: Scanning /home/hero1900/Desktop/lg-live-0.9.4/[BOOT]
BraseroGrowisofs stderr: Writing:   Initial Padblock                        Start Block 0
BraseroGrowisofs stderr: Done with: Initial Padblock                        Block(s)    16
BraseroGrowisofs stderr: Writing:   Primary Volume Descriptor               Start Block 16
BraseroGrowisofs stderr: Done with: Primary Volume Descriptor               Block(s)    1
BraseroGrowisofs stderr: Writing:   End Volume Descriptor                   Start Block 17
BraseroGrowisofs stderr: Done with: End Volume Descriptor                   Block(s)    1
BraseroGrowisofs stderr: Writing:   UDF volume recognition area             Start Block 18
BraseroGrowisofs stderr: Done with: UDF volume recognition area             Block(s)    3
BraseroGrowisofs stderr: Writing:   Version block                           Start Block 21
BraseroGrowisofs stderr: Done with: Version block                           Block(s)    1
BraseroGrowisofs stderr: Writing:   UDF pad to sector 32                    Start Block 22
BraseroGrowisofs stderr: Done with: UDF pad to sector 32                    Block(s)    10
BraseroGrowisofs stderr: Writing:   UDF main seq                            Start Block 32
BraseroGrowisofs stderr: Done with: UDF main seq                            Block(s)    16
BraseroGrowisofs stderr: Writing:   UDF second seq                          Start Block 48
BraseroGrowisofs stderr: Done with: UDF second seq                          Block(s)    16
BraseroGrowisofs stderr: Writing:   UDF integ seq                           Start Block 64
BraseroGrowisofs stderr: Done with: UDF integ seq                           Block(s)    2
BraseroGrowisofs stderr: Writing:   UDF pad to sector 256                   Start Block 66
BraseroGrowisofs stderr: Done with: UDF pad to sector 256                   Block(s)    190
BraseroGrowisofs stderr: Writing:   UDF Anchor volume                       Start Block 256
BraseroGrowisofs stderr: Done with: UDF Anchor volume                       Block(s)    1
BraseroGrowisofs stderr: Writing:   UDF file set                            Start Block 257
BraseroGrowisofs stderr: Done with: UDF file set                            Block(s)    2
BraseroGrowisofs stderr: Writing:   UDF directory tree                      Start Block 259
BraseroGrowisofs stderr: Done with: UDF directory tree                      Block(s)    4
BraseroGrowisofs stderr: Writing:   UDF file entries                        Start Block 263
BraseroGrowisofs stderr: Done with: UDF file entries                        Block(s)    12
BraseroGrowisofs stderr: Writing:   Path table                              Start Block 275
BraseroGrowisofs stderr: Done with: Path table                              Block(s)    4
BraseroGrowisofs stderr: Writing:   Directory tree                          Start Block 279
BraseroGrowisofs stderr: Done with: Directory tree                          Block(s)    2
BraseroGrowisofs stderr: Writing:   Directory tree cleanup                  Start Block 281
BraseroGrowisofs stderr: Done with: Directory tree cleanup                  Block(s)    0
BraseroGrowisofs stderr: Writing:   Extension record                        Start Block 281
BraseroGrowisofs stderr: Done with: Extension record                        Block(s)    1
BraseroGrowisofs stderr: Writing:   The File(s)                             Start Block 282
BraseroGrowisofs stderr:   0.31% done, estimate finish Thu Jun 18 16:54:43 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   0.63% done, estimate finish Thu Jun 18 16:57:22 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr:   0.94% done, estimate finish Thu Jun 18 16:56:29 2009
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr: /dev/sr0: "Current Write Speed" is 8.2x1352KBps.
BraseroGrowisofs stderr: :-[ WRITE@LBA=3b0h failed with SK=3h/WRITE ERROR]: Input/output error
BraseroGrowisofs stderr: :-( write failed: Input/output error
BraseroGrowisofs stderr: /dev/sr0: flushing cache
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr: /dev/sr0: closing track
BraseroGrowisofs stderr: /dev/sr0: closing disc
BraseroGrowisofs stderr: :-[ CLOSE DISC failed with SK=3h/POSITIONING ERROR DETECTED BY READ OF MEDIUM]: Input/output error
BraseroGrowisofs stdout: HUP
BraseroGrowisofs stderr: HUP
BraseroGrowisofs process finished with status 5
BraseroGrowisofs called brasero_job_error
BraseroGrowisofs finished with an error
BraseroGrowisofs asked to stop because of an error
    error        = 0
    message    = "no message"
BraseroGrowisofs stopping
BraseroGrowisofs got killed
Session error : unknown (brasero_burn_record burn.c:2602)

---

### Post by hero1900 on 2009-06-18
in summury i have this output

[B]Executing 'builtin_dd if=/home/hero1900/Desktop/lg-live-0.9.4.iso of=/dev/sr0 obs=32k seek=0'
/dev/sr0: "Current Write Speed" is 6.1x1352KBps.
:-[ WRITE@LBA=310h failed with SK=3h/WRITE ERROR]: Input/output error
:-( write failed: Input/output error
/dev/sr0: flushing cache
/dev/sr0: closing track
/dev/sr0: closing disc

only facing it on ubuntu
i can burn using nero in windows without any problem i just try it

[/B]

---

### Post by wpshooter on 2009-06-18
When did this start ?

---

### Post by hero1900 on 2009-06-19
i don't really know when??
i just want to burn an image to a dvd then i notice that it gave me an error 
now after some test i found that it is not an ununtu problem its windows also
so i think it is my dvd drive and also today i try to burn it again a sound like zzzzzzzzzzzzzzzzz get out from speakers, i dont really know what is the problem exactlly
i hope it is only dvd drive problem (at least i can change) but that sound make me think about motherboard or main chip

[-o< so any one could help??

---

### Post by synapsys on 2009-06-19
Just buy a new dvd drive. They are cheap and easily replaced. Plus if you need to buy a new computer you can bring it with you. If you are hearing a constant buzz or hum from speakers regardless of operating system, then the problem is your sound card. If you don't have a sound card e.g. (integrated into the motherboard) then you will need to replace the mobo. If you don't feel comfortable replacing a motherboard DON'T DO IT. Take it to a professional.

---

