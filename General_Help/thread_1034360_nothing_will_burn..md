---
title: "nothing will burn."
date: 2009-01-08
forum: General Help
---

### Post by leveliv on 2009-01-08
I've never successfully burnt anything yet on my install of Ubuntu here's my Debugging log from my most recent attempt

```
Checking session consistency (brasero_burn_check_session_consistency burn.c:1843)
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_set_output_size_for_current_track
BraseroLocalTrack stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
BraseroLocalTrack no foreign URIs
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
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_input_type
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles called brasero_job_set_current_action
BraseroChecksumFiles called brasero_job_start_progress
BraseroChecksumFiles Called brasero_job_set_progress (0.055556)
BraseroChecksumFiles Called brasero_job_set_progress (0.111111)
BraseroChecksumFiles Called brasero_job_set_progress (0.166667)
BraseroChecksumFiles Called brasero_job_set_progress (0.222222)
BraseroChecksumFiles Called brasero_job_set_progress (0.277778)
BraseroChecksumFiles Called brasero_job_set_progress (0.333333)
BraseroChecksumFiles Called brasero_job_set_progress (0.388889)
BraseroChecksumFiles Called brasero_job_set_progress (0.444444)
BraseroChecksumFiles Called brasero_job_set_progress (0.500000)
BraseroChecksumFiles Called brasero_job_set_progress (0.555556)
BraseroChecksumFiles Called brasero_job_set_progress (0.611111)
BraseroChecksumFiles Called brasero_job_set_progress (0.666667)
BraseroChecksumFiles Called brasero_job_set_progress (0.722222)
BraseroChecksumFiles Called brasero_job_set_progress (0.777778)
BraseroChecksumFiles Called brasero_job_set_progress (0.833333)
BraseroChecksumFiles Called brasero_job_set_progress (0.888889)
BraseroChecksumFiles Called brasero_job_set_progress (0.944444)
BraseroChecksumFiles Called brasero_job_set_progress (1.000000)
BraseroChecksumFiles called brasero_job_get_flags
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_input_type
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles Adding graft for checksum file /.checksum.md5 file:///tmp/brasero_tmp_5RWQNU.md5
BraseroChecksumFiles called brasero_job_add_track
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles finished track successfully
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
	-use-the-force-luke=dao
	-dvd-compat
	-speed=7
	-use-the-force-luke=tty
	-Z
	/dev/scd0
	-dry-run
	-r
	-J
	-input-charset
	utf8
	-graft-points
	-path-list
	/tmp/brasero_tmp_CT19MU
	-exclude-list
	/tmp/brasero_tmp_4PDRNU
	-print-size
BraseroGrowisofs launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stdout: Executing 'genisoimage -r -J -input-charset utf8 -graft-points -path-list /tmp/brasero_tmp_CT19MU -exclude-list /tmp/brasero_tmp_4PDRNU -print-size | builtin_dd of=/dev/scd0 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous
BraseroGrowisofs stderr: Using CAPTA000.AVI;1 for  Captain Planet/Captain Planet - 114 - Meltdown  Syndrome.avi (Captain Planet - 107 - Last Of Her Kind.avi)
BraseroGrowisofs stderr: Using CAPTA001.AVI;1 for  Captain Planet/Captain Planet - 107 - Last Of Her Kind.avi (Captain Planet - 118 - Kwame's Crisis.avi)
BraseroGrowisofs stderr: Using CAPTA002.AVI;1 for  Captain Planet/Captain Planet - 118 - Kwame's Crisis.avi (Captain Planet - 108 - The Dead Seas.avi)
BraseroGrowisofs stderr: Using CAPTA003.AVI;1 for  Captain Planet/Captain Planet - 108 - The Dead Seas.avi (Captain Planet - 112 - A World Below Us.avi)
BraseroGrowisofs stderr: Using CAPTA004.AVI;1 for  Captain Planet/Captain Planet - 112 - A World Below Us.avi (Captain Planet - 101 - A Hero For Earth.avi)
BraseroGrowisofs stderr: Using CAPTA005.AVI;1 for  Captain Planet/Captain Planet - 101 - A Hero For Earth.avi (Captain Planet - 113 - Plunder Dam.avi)
BraseroGrowisofs stderr: Using CAPTA006.AVI;1 for  Captain Planet/Captain Planet - 113 - Plunder Dam.avi (Captain Planet - 102 - Rain of Terror.avi)
BraseroGrowisofs stderr: Using CAPTA007.AVI;1 for  Captain Planet/Captain Planet - 102 - Rain of Terror.avi (Captain Planet - 111 - The Littlest Planeteer.avi)
BraseroGrowisofs stderr: Using CAPTA008.AVI;1 for  Captain Planet/Captain Planet - 111 - The Littlest Planeteer.avi (Captain Planet - 106 - The Conqueror.avi)
BraseroGrowisofs stderr: Using CAPTA009.AVI;1 for  Captain Planet/Captain Planet - 106 - The Conqueror.avi (Captain Planet - 105 - Deadly Ransom.avi)
BraseroGrowisofs stderr: Using CAPTA00A.AVI;1 for  Captain Planet/Captain Planet - 105 - Deadly Ransom.avi (Captain Planet - 109 - Tree Of Life.avi)
BraseroGrowisofs stderr: Using CAPTA00B.AVI;1 for  Captain Planet/Captain Planet - 109 - Tree Of Life.avi (Captain Planet - 103 - Beast of The Temple.avi)
BraseroGrowisofs stderr: Using CAPTA00C.AVI;1 for  Captain Planet/Captain Planet - 103 - Beast of The Temple.avi (Captain Planet - 115 - Smog Hog.avi)
BraseroGrowisofs stderr: Using CAPTA00D.AVI;1 for  Captain Planet/Captain Planet - 115 - Smog Hog.avi (Captain Planet - 110 - Volcano's Wrath.avi)
BraseroGrowisofs stderr: Using CAPTA00E.AVI;1 for  Captain Planet/Captain Planet - 110 - Volcano's Wrath.avi (Captain Planet - 104 - Skumm Lord.avi)
BraseroGrowisofs stderr: Using CAPTA00F.AVI;1 for  Captain Planet/Captain Planet - 104 - Skumm Lord.avi (Captain Planet - 116 - Polluting By Computer.avi)
BraseroGrowisofs stderr: Total extents scheduled to be written = 1501009
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_output_size_for_current_track
BraseroGrowisofs finished successfully session
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
	-use-the-force-luke=dao
	-dvd-compat
	-speed=7
	-use-the-force-luke=tracksize:1501009
	-use-the-force-luke=tty
	-Z
	/dev/scd0
	-r
	-J
	-input-charset
	utf8
	-graft-points
	-path-list
	/tmp/brasero_tmp_4HJTNU
	-exclude-list
	/tmp/brasero_tmp_XKJTNU
	-V
	Data disc (08 Jan 09)
	-A
	Brasero-0.8.2
	-sysid
	LINUX
	-v
BraseroGrowisofs launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stderr: genisoimage 1.1.8 (Linux)
BraseroGrowisofs stdout: Executing 'genisoimage -r -J -input-charset utf8 -graft-points -path-list /tmp/brasero_tmp_4HJTNU -exclude-list /tmp/brasero_tmp_XKJTNU -V Data disc (08 Jan 09) -A Brasero-0.8.2 -sysid LINUX -v | builtin_dd of=/dev/scd0 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous
BraseroGrowisofs stderr: Scanning /home/chris/Azureus Downloads/Captain Planet
BraseroGrowisofs stderr: Using CAPTA000.AVI;1 for  Captain Planet/Captain Planet - 114 - Meltdown  Syndrome.avi (Captain Planet - 107 - Last Of Her Kind.avi)
BraseroGrowisofs stderr: Using CAPTA001.AVI;1 for  Captain Planet/Captain Planet - 107 - Last Of Her Kind.avi (Captain Planet - 118 - Kwame's Crisis.avi)
BraseroGrowisofs stderr: Using CAPTA002.AVI;1 for  Captain Planet/Captain Planet - 118 - Kwame's Crisis.avi (Captain Planet - 108 - The Dead Seas.avi)
BraseroGrowisofs stderr: Using CAPTA003.AVI;1 for  Captain Planet/Captain Planet - 108 - The Dead Seas.avi (Captain Planet - 112 - A World Below Us.avi)
BraseroGrowisofs stderr: Using CAPTA004.AVI;1 for  Captain Planet/Captain Planet - 112 - A World Below Us.avi (Captain Planet - 101 - A Hero For Earth.avi)
BraseroGrowisofs stderr: Using CAPTA005.AVI;1 for  Captain Planet/Captain Planet - 101 - A Hero For Earth.avi (Captain Planet - 113 - Plunder Dam.avi)
BraseroGrowisofs stderr: Using CAPTA006.AVI;1 for  Captain Planet/Captain Planet - 113 - Plunder Dam.avi (Captain Planet - 102 - Rain of Terror.avi)
BraseroGrowisofs stderr: Using CAPTA007.AVI;1 for  Captain Planet/Captain Planet - 102 - Rain of Terror.avi (Captain Planet - 111 - The Littlest Planeteer.avi)
BraseroGrowisofs stderr: Using CAPTA008.AVI;1 for  Captain Planet/Captain Planet - 111 - The Littlest Planeteer.avi (Captain Planet - 106 - The Conqueror.avi)
BraseroGrowisofs stderr: Using CAPTA009.AVI;1 for  Captain Planet/Captain Planet - 106 - The Conqueror.avi (Captain Planet - 105 - Deadly Ransom.avi)
BraseroGrowisofs stderr: Using CAPTA00A.AVI;1 for  Captain Planet/Captain Planet - 105 - Deadly Ransom.avi (Captain Planet - 109 - Tree Of Life.avi)
BraseroGrowisofs stderr: Using CAPTA00B.AVI;1 for  Captain Planet/Captain Planet - 109 - Tree Of Life.avi (Captain Planet - 103 - Beast of The Temple.avi)
BraseroGrowisofs stderr: Using CAPTA00C.AVI;1 for  Captain Planet/Captain Planet - 103 - Beast of The Temple.avi (Captain Planet - 115 - Smog Hog.avi)
BraseroGrowisofs stderr: Using CAPTA00D.AVI;1 for  Captain Planet/Captain Planet - 115 - Smog Hog.avi (Captain Planet - 110 - Volcano's Wrath.avi)
BraseroGrowisofs stderr: Using CAPTA00E.AVI;1 for  Captain Planet/Captain Planet - 110 - Volcano's Wrath.avi (Captain Planet - 104 - Skumm Lord.avi)
BraseroGrowisofs stderr: Using CAPTA00F.AVI;1 for  Captain Planet/Captain Planet - 104 - Skumm Lord.avi (Captain Planet - 116 - Polluting By Computer.avi)
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
BraseroGrowisofs stderr: Done with: Directory tree                          Block(s)    3
BraseroGrowisofs stderr: Writing:   Joliet directory tree                   Start Block 31
BraseroGrowisofs stderr: Done with: Joliet directory tree                   Block(s)    3
BraseroGrowisofs stderr: Writing:   Directory tree cleanup                  Start Block 34
BraseroGrowisofs stderr: Done with: Directory tree cleanup                  Block(s)    0
BraseroGrowisofs stderr: Writing:   Extension record                        Start Block 34
BraseroGrowisofs stderr: Done with: Extension record                        Block(s)    1
BraseroGrowisofs stderr: Writing:   The File(s)                             Start Block 35
BraseroGrowisofs stderr:   0.33% done, estimate finish Thu Jan  8 08:40:26 2009
BraseroGrowisofs Called brasero_job_set_progress (0.003300)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:   0.67% done, estimate finish Thu Jan  8 08:40:26 2009
BraseroGrowisofs Called brasero_job_set_progress (0.006700)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:   1.00% done, estimate finish Thu Jan  8 08:40:26 2009
BraseroGrowisofs Called brasero_job_set_progress (0.010000)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr: /dev/scd0: engaging DVD-R DAO upon user request...
BraseroGrowisofs stderr: /dev/scd0: reserving 1501009 blocks
BraseroGrowisofs stderr: /dev/scd0: "Current Write Speed" is 8.2x1352KBps.
BraseroGrowisofs stderr:   1.33% done, estimate finish Thu Jan  8 10:15:28 2009
BraseroGrowisofs Called brasero_job_set_progress (0.013300)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:   1.67% done, estimate finish Thu Jan  8 09:58:26 2009
BraseroGrowisofs Called brasero_job_set_progress (0.016700)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:   2.00% done, estimate finish Thu Jan  8 09:47:08 2009
BraseroGrowisofs Called brasero_job_set_progress (0.020000)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:   2.33% done, estimate finish Thu Jan  8 09:39:01 2009
BraseroGrowisofs Called brasero_job_set_progress (0.023300)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:   2.67% done, estimate finish Thu Jan  8 09:33:35 2009
BraseroGrowisofs Called brasero_job_set_progress (0.026700)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:   3.00% done, estimate finish Thu Jan  8 09:28:47 2009
BraseroGrowisofs Called brasero_job_set_progress (0.030000)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:   3.33% done, estimate finish Thu Jan  8 09:24:57 2009
BraseroGrowisofs Called brasero_job_set_progress (0.033300)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:   3.67% done, estimate finish Thu Jan  8 09:21:48 2009
BraseroGrowisofs Called brasero_job_set_progress (0.036700)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:   4.00% done, estimate finish Thu Jan  8 09:19:12 2009
BraseroGrowisofs Called brasero_job_set_progress (0.040000)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:   4.33% done, estimate finish Thu Jan  8 09:16:59 2009
BraseroGrowisofs Called brasero_job_set_progress (0.043300)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:   4.66% done, estimate finish Thu Jan  8 09:15:05 2009
BraseroGrowisofs Called brasero_job_set_progress (0.046600)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:   5.00% done, estimate finish Thu Jan  8 09:13:27 2009
BraseroGrowisofs Called brasero_job_set_progress (0.050000)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:   5.33% done, estimate finish Thu Jan  8 09:12:00 2009
BraseroGrowisofs Called brasero_job_set_progress (0.053300)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:   5.66% done, estimate finish Thu Jan  8 09:10:44 2009
BraseroGrowisofs Called brasero_job_set_progress (0.056600)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:   6.00% done, estimate finish Thu Jan  8 09:09:37 2009
BraseroGrowisofs Called brasero_job_set_progress (0.060000)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:   6.33% done, estimate finish Thu Jan  8 09:08:36 2009
BraseroGrowisofs Called brasero_job_set_progress (0.063300)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:   6.66% done, estimate finish Thu Jan  8 09:07:42 2009
BraseroGrowisofs Called brasero_job_set_progress (0.066600)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:   7.00% done, estimate finish Thu Jan  8 09:07:06 2009
BraseroGrowisofs Called brasero_job_set_progress (0.070000)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:   7.33% done, estimate finish Thu Jan  8 09:06:21 2009
BraseroGrowisofs Called brasero_job_set_progress (0.073300)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:   7.66% done, estimate finish Thu Jan  8 09:05:39 2009
BraseroGrowisofs Called brasero_job_set_progress (0.076600)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:   7.99% done, estimate finish Thu Jan  8 09:05:01 2009
BraseroGrowisofs Called brasero_job_set_progress (0.079900)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:   8.33% done, estimate finish Thu Jan  8 09:04:14 2009
BraseroGrowisofs Called brasero_job_set_progress (0.083300)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:   8.66% done, estimate finish Thu Jan  8 09:03:43 2009
BraseroGrowisofs Called brasero_job_set_progress (0.086600)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:   8.99% done, estimate finish Thu Jan  8 09:03:13 2009
BraseroGrowisofs Called brasero_job_set_progress (0.089900)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:   9.33% done, estimate finish Thu Jan  8 09:02:46 2009
BraseroGrowisofs Called brasero_job_set_progress (0.093300)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:   9.66% done, estimate finish Thu Jan  8 09:02:20 2009
BraseroGrowisofs Called brasero_job_set_progress (0.096600)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:   9.99% done, estimate finish Thu Jan  8 09:01:56 2009
BraseroGrowisofs Called brasero_job_set_progress (0.099900)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  10.33% done, estimate finish Thu Jan  8 09:01:34 2009
BraseroGrowisofs Called brasero_job_set_progress (0.103300)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  10.66% done, estimate finish Thu Jan  8 09:01:13 2009
BraseroGrowisofs Called brasero_job_set_progress (0.106600)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  10.99% done, estimate finish Thu Jan  8 09:00:54 2009
BraseroGrowisofs Called brasero_job_set_progress (0.109900)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  11.33% done, estimate finish Thu Jan  8 09:00:35 2009
BraseroGrowisofs Called brasero_job_set_progress (0.113300)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  11.66% done, estimate finish Thu Jan  8 09:00:18 2009
BraseroGrowisofs Called brasero_job_set_progress (0.116600)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  11.99% done, estimate finish Thu Jan  8 09:00:01 2009
BraseroGrowisofs Called brasero_job_set_progress (0.119900)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  12.33% done, estimate finish Thu Jan  8 08:59:46 2009
BraseroGrowisofs Called brasero_job_set_progress (0.123300)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  12.66% done, estimate finish Thu Jan  8 08:59:23 2009
BraseroGrowisofs Called brasero_job_set_progress (0.126600)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  12.99% done, estimate finish Thu Jan  8 08:59:09 2009
BraseroGrowisofs Called brasero_job_set_progress (0.129900)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  13.32% done, estimate finish Thu Jan  8 08:59:11 2009
BraseroGrowisofs Called brasero_job_set_progress (0.133200)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  13.66% done, estimate finish Thu Jan  8 08:58:51 2009
BraseroGrowisofs Called brasero_job_set_progress (0.136600)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  13.99% done, estimate finish Thu Jan  8 08:58:39 2009
BraseroGrowisofs Called brasero_job_set_progress (0.139900)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  14.32% done, estimate finish Thu Jan  8 08:58:28 2009
BraseroGrowisofs Called brasero_job_set_progress (0.143200)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  14.66% done, estimate finish Thu Jan  8 08:58:17 2009
BraseroGrowisofs Called brasero_job_set_progress (0.146600)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  14.99% done, estimate finish Thu Jan  8 08:58:06 2009
BraseroGrowisofs Called brasero_job_set_progress (0.149900)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  15.32% done, estimate finish Thu Jan  8 08:57:56 2009
BraseroGrowisofs Called brasero_job_set_progress (0.153200)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  15.66% done, estimate finish Thu Jan  8 08:57:40 2009
BraseroGrowisofs Called brasero_job_set_progress (0.156600)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  15.99% done, estimate finish Thu Jan  8 08:57:31 2009
BraseroGrowisofs Called brasero_job_set_progress (0.159900)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  16.32% done, estimate finish Thu Jan  8 08:57:22 2009
BraseroGrowisofs Called brasero_job_set_progress (0.163200)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  16.66% done, estimate finish Thu Jan  8 08:57:14 2009
BraseroGrowisofs Called brasero_job_set_progress (0.166600)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  16.99% done, estimate finish Thu Jan  8 08:57:06 2009
BraseroGrowisofs Called brasero_job_set_progress (0.169900)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  17.32% done, estimate finish Thu Jan  8 08:56:53 2009
BraseroGrowisofs Called brasero_job_set_progress (0.173200)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  17.66% done, estimate finish Thu Jan  8 08:56:45 2009
BraseroGrowisofs Called brasero_job_set_progress (0.176600)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  17.99% done, estimate finish Thu Jan  8 08:56:38 2009
BraseroGrowisofs Called brasero_job_set_progress (0.179900)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  18.32% done, estimate finish Thu Jan  8 08:56:32 2009
BraseroGrowisofs Called brasero_job_set_progress (0.183200)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  18.65% done, estimate finish Thu Jan  8 08:56:20 2009
BraseroGrowisofs Called brasero_job_set_progress (0.186500)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  18.99% done, estimate finish Thu Jan  8 08:56:13 2009
BraseroGrowisofs Called brasero_job_set_progress (0.189900)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  19.32% done, estimate finish Thu Jan  8 08:56:08 2009
BraseroGrowisofs Called brasero_job_set_progress (0.193200)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  19.65% done, estimate finish Thu Jan  8 08:56:02 2009
BraseroGrowisofs Called brasero_job_set_progress (0.196500)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  19.99% done, estimate finish Thu Jan  8 08:55:51 2009
BraseroGrowisofs Called brasero_job_set_progress (0.199900)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  20.32% done, estimate finish Thu Jan  8 08:55:46 2009
BraseroGrowisofs Called brasero_job_set_progress (0.203200)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  20.65% done, estimate finish Thu Jan  8 08:55:41 2009
BraseroGrowisofs Called brasero_job_set_progress (0.206500)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  20.99% done, estimate finish Thu Jan  8 08:55:36 2009
BraseroGrowisofs Called brasero_job_set_progress (0.209900)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  21.32% done, estimate finish Thu Jan  8 08:55:26 2009
BraseroGrowisofs Called brasero_job_set_progress (0.213200)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  21.65% done, estimate finish Thu Jan  8 08:55:21 2009
BraseroGrowisofs Called brasero_job_set_progress (0.216500)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  21.99% done, estimate finish Thu Jan  8 08:55:17 2009
BraseroGrowisofs Called brasero_job_set_progress (0.219900)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  22.32% done, estimate finish Thu Jan  8 08:55:08 2009
BraseroGrowisofs Called brasero_job_set_progress (0.223200)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  22.65% done, estimate finish Thu Jan  8 08:55:04 2009
BraseroGrowisofs Called brasero_job_set_progress (0.226500)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  22.98% done, estimate finish Thu Jan  8 08:55:00 2009
BraseroGrowisofs Called brasero_job_set_progress (0.229800)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  23.32% done, estimate finish Thu Jan  8 08:54:52 2009
BraseroGrowisofs Called brasero_job_set_progress (0.233200)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  23.65% done, estimate finish Thu Jan  8 08:54:48 2009
BraseroGrowisofs Called brasero_job_set_progress (0.236500)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  23.98% done, estimate finish Thu Jan  8 08:54:44 2009
BraseroGrowisofs Called brasero_job_set_progress (0.239800)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  24.32% done, estimate finish Thu Jan  8 08:54:37 2009
BraseroGrowisofs Called brasero_job_set_progress (0.243200)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  24.65% done, estimate finish Thu Jan  8 08:54:33 2009
BraseroGrowisofs Called brasero_job_set_progress (0.246500)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  24.98% done, estimate finish Thu Jan  8 08:54:30 2009
BraseroGrowisofs Called brasero_job_set_progress (0.249800)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  25.32% done, estimate finish Thu Jan  8 08:54:23 2009
BraseroGrowisofs Called brasero_job_set_progress (0.253200)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  25.65% done, estimate finish Thu Jan  8 08:54:20 2009
BraseroGrowisofs Called brasero_job_set_progress (0.256500)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  25.98% done, estimate finish Thu Jan  8 08:54:17 2009
BraseroGrowisofs Called brasero_job_set_progress (0.259800)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  26.32% done, estimate finish Thu Jan  8 08:54:10 2009
BraseroGrowisofs Called brasero_job_set_progress (0.263200)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  26.65% done, estimate finish Thu Jan  8 08:54:07 2009
BraseroGrowisofs Called brasero_job_set_progress (0.266500)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  26.98% done, estimate finish Thu Jan  8 08:54:05 2009
BraseroGrowisofs Called brasero_job_set_progress (0.269800)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  27.32% done, estimate finish Thu Jan  8 08:53:58 2009
BraseroGrowisofs Called brasero_job_set_progress (0.273200)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  27.65% done, estimate finish Thu Jan  8 08:53:56 2009
BraseroGrowisofs Called brasero_job_set_progress (0.276500)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  27.98% done, estimate finish Thu Jan  8 08:53:50 2009
BraseroGrowisofs Called brasero_job_set_progress (0.279800)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  28.31% done, estimate finish Thu Jan  8 08:53:47 2009
BraseroGrowisofs Called brasero_job_set_progress (0.283100)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  28.65% done, estimate finish Thu Jan  8 08:53:45 2009
BraseroGrowisofs Called brasero_job_set_progress (0.286500)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  28.98% done, estimate finish Thu Jan  8 08:53:39 2009
BraseroGrowisofs Called brasero_job_set_progress (0.289800)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  29.31% done, estimate finish Thu Jan  8 08:53:37 2009
BraseroGrowisofs Called brasero_job_set_progress (0.293100)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  29.65% done, estimate finish Thu Jan  8 08:53:31 2009
BraseroGrowisofs Called brasero_job_set_progress (0.296500)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  29.98% done, estimate finish Thu Jan  8 08:53:29 2009
BraseroGrowisofs Called brasero_job_set_progress (0.299800)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  30.31% done, estimate finish Thu Jan  8 08:53:27 2009
BraseroGrowisofs Called brasero_job_set_progress (0.303100)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  30.65% done, estimate finish Thu Jan  8 08:53:22 2009
BraseroGrowisofs Called brasero_job_set_progress (0.306500)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  30.98% done, estimate finish Thu Jan  8 08:53:20 2009
BraseroGrowisofs Called brasero_job_set_progress (0.309800)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  31.31% done, estimate finish Thu Jan  8 08:53:15 2009
BraseroGrowisofs Called brasero_job_set_progress (0.313100)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  31.65% done, estimate finish Thu Jan  8 08:53:13 2009
BraseroGrowisofs Called brasero_job_set_progress (0.316500)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  31.98% done, estimate finish Thu Jan  8 08:53:09 2009
BraseroGrowisofs Called brasero_job_set_progress (0.319800)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  32.31% done, estimate finish Thu Jan  8 08:53:07 2009
BraseroGrowisofs Called brasero_job_set_progress (0.323100)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  32.65% done, estimate finish Thu Jan  8 08:53:02 2009
BraseroGrowisofs Called brasero_job_set_progress (0.326500)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  32.98% done, estimate finish Thu Jan  8 08:53:01 2009
BraseroGrowisofs Called brasero_job_set_progress (0.329800)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  33.31% done, estimate finish Thu Jan  8 08:52:59 2009
BraseroGrowisofs Called brasero_job_set_progress (0.333100)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  33.64% done, estimate finish Thu Jan  8 08:52:55 2009
BraseroGrowisofs Called brasero_job_set_progress (0.336400)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  33.98% done, estimate finish Thu Jan  8 08:52:53 2009
BraseroGrowisofs Called brasero_job_set_progress (0.339800)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  34.31% done, estimate finish Thu Jan  8 08:52:49 2009
BraseroGrowisofs Called brasero_job_set_progress (0.343100)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  34.64% done, estimate finish Thu Jan  8 08:52:47 2009
BraseroGrowisofs Called brasero_job_set_progress (0.346400)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  34.98% done, estimate finish Thu Jan  8 08:52:43 2009
BraseroGrowisofs Called brasero_job_set_progress (0.349800)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  35.31% done, estimate finish Thu Jan  8 08:52:42 2009
BraseroGrowisofs Called brasero_job_set_progress (0.353100)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  35.64% done, estimate finish Thu Jan  8 08:52:38 2009
BraseroGrowisofs Called brasero_job_set_progress (0.356400)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  35.98% done, estimate finish Thu Jan  8 08:52:37 2009
BraseroGrowisofs Called brasero_job_set_progress (0.359800)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  36.31% done, estimate finish Thu Jan  8 08:52:33 2009
BraseroGrowisofs Called brasero_job_set_progress (0.363100)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  36.64% done, estimate finish Thu Jan  8 08:52:31 2009
BraseroGrowisofs Called brasero_job_set_progress (0.366400)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  36.98% done, estimate finish Thu Jan  8 08:52:28 2009
BraseroGrowisofs Called brasero_job_set_progress (0.369800)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  37.31% done, estimate finish Thu Jan  8 08:52:27 2009
BraseroGrowisofs Called brasero_job_set_progress (0.373100)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  37.64% done, estimate finish Thu Jan  8 08:52:23 2009
BraseroGrowisofs Called brasero_job_set_progress (0.376400)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  37.98% done, estimate finish Thu Jan  8 08:52:24 2009
BraseroGrowisofs Called brasero_job_set_progress (0.379800)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  38.31% done, estimate finish Thu Jan  8 08:52:23 2009
BraseroGrowisofs Called brasero_job_set_progress (0.383100)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  38.64% done, estimate finish Thu Jan  8 08:52:20 2009
BraseroGrowisofs Called brasero_job_set_progress (0.386400)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  38.97% done, estimate finish Thu Jan  8 08:52:19 2009
BraseroGrowisofs Called brasero_job_set_progress (0.389700)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  39.31% done, estimate finish Thu Jan  8 08:52:15 2009
BraseroGrowisofs Called brasero_job_set_progress (0.393100)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  39.64% done, estimate finish Thu Jan  8 08:52:14 2009
BraseroGrowisofs Called brasero_job_set_progress (0.396400)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  39.97% done, estimate finish Thu Jan  8 08:52:11 2009
BraseroGrowisofs Called brasero_job_set_progress (0.399700)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  40.31% done, estimate finish Thu Jan  8 08:52:10 2009
BraseroGrowisofs Called brasero_job_set_progress (0.403100)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  40.64% done, estimate finish Thu Jan  8 08:52:07 2009
BraseroGrowisofs Called brasero_job_set_progress (0.406400)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  40.97% done, estimate finish Thu Jan  8 08:52:06 2009
BraseroGrowisofs Called brasero_job_set_progress (0.409700)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  41.31% done, estimate finish Thu Jan  8 08:52:03 2009
BraseroGrowisofs Called brasero_job_set_progress (0.413100)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  41.64% done, estimate finish Thu Jan  8 08:52:00 2009
BraseroGrowisofs Called brasero_job_set_progress (0.416400)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  41.97% done, estimate finish Thu Jan  8 08:51:59 2009
BraseroGrowisofs Called brasero_job_set_progress (0.419700)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  42.31% done, estimate finish Thu Jan  8 08:51:56 2009
BraseroGrowisofs Called brasero_job_set_progress (0.423100)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  42.64% done, estimate finish Thu Jan  8 08:51:55 2009
BraseroGrowisofs Called brasero_job_set_progress (0.426400)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  42.97% done, estimate finish Thu Jan  8 08:51:52 2009
BraseroGrowisofs Called brasero_job_set_progress (0.429700)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  43.30% done, estimate finish Thu Jan  8 08:51:51 2009
BraseroGrowisofs Called brasero_job_set_progress (0.433000)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  43.64% done, estimate finish Thu Jan  8 08:51:48 2009
BraseroGrowisofs Called brasero_job_set_progress (0.436400)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  43.97% done, estimate finish Thu Jan  8 08:51:48 2009
BraseroGrowisofs Called brasero_job_set_progress (0.439700)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  44.30% done, estimate finish Thu Jan  8 08:51:45 2009
BraseroGrowisofs Called brasero_job_set_progress (0.443000)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  44.64% done, estimate finish Thu Jan  8 08:51:42 2009
BraseroGrowisofs Called brasero_job_set_progress (0.446400)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  44.97% done, estimate finish Thu Jan  8 08:51:42 2009
BraseroGrowisofs Called brasero_job_set_progress (0.449700)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  45.30% done, estimate finish Thu Jan  8 08:51:39 2009
BraseroGrowisofs Called brasero_job_set_progress (0.453000)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  45.64% done, estimate finish Thu Jan  8 08:51:38 2009
BraseroGrowisofs Called brasero_job_set_progress (0.456400)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  45.97% done, estimate finish Thu Jan  8 08:51:36 2009
BraseroGrowisofs Called brasero_job_set_progress (0.459700)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  46.30% done, estimate finish Thu Jan  8 08:51:33 2009
BraseroGrowisofs Called brasero_job_set_progress (0.463000)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  46.64% done, estimate finish Thu Jan  8 08:51:32 2009
BraseroGrowisofs Called brasero_job_set_progress (0.466400)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  46.97% done, estimate finish Thu Jan  8 08:51:30 2009
BraseroGrowisofs Called brasero_job_set_progress (0.469700)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  47.30% done, estimate finish Thu Jan  8 08:51:29 2009
BraseroGrowisofs Called brasero_job_set_progress (0.473000)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  47.64% done, estimate finish Thu Jan  8 08:51:27 2009
BraseroGrowisofs Called brasero_job_set_progress (0.476400)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  47.97% done, estimate finish Thu Jan  8 08:51:24 2009
BraseroGrowisofs Called brasero_job_set_progress (0.479700)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  48.30% done, estimate finish Thu Jan  8 08:51:24 2009
BraseroGrowisofs Called brasero_job_set_progress (0.483000)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  48.63% done, estimate finish Thu Jan  8 08:51:21 2009
BraseroGrowisofs Called brasero_job_set_progress (0.486300)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  48.97% done, estimate finish Thu Jan  8 08:51:21 2009
BraseroGrowisofs Called brasero_job_set_progress (0.489700)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  49.30% done, estimate finish Thu Jan  8 08:51:19 2009
BraseroGrowisofs Called brasero_job_set_progress (0.493000)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  49.63% done, estimate finish Thu Jan  8 08:51:16 2009
BraseroGrowisofs Called brasero_job_set_progress (0.496300)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  49.97% done, estimate finish Thu Jan  8 08:51:16 2009
BraseroGrowisofs Called brasero_job_set_progress (0.499700)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  50.30% done, estimate finish Thu Jan  8 08:51:14 2009
BraseroGrowisofs Called brasero_job_set_progress (0.503000)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  50.63% done, estimate finish Thu Jan  8 08:51:11 2009
BraseroGrowisofs Called brasero_job_set_progress (0.506300)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  50.97% done, estimate finish Thu Jan  8 08:51:11 2009
BraseroGrowisofs Called brasero_job_set_progress (0.509700)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  51.30% done, estimate finish Thu Jan  8 08:51:09 2009
BraseroGrowisofs Called brasero_job_set_progress (0.513000)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  51.63% done, estimate finish Thu Jan  8 08:51:07 2009
BraseroGrowisofs Called brasero_job_set_progress (0.516300)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  51.97% done, estimate finish Thu Jan  8 08:51:06 2009
BraseroGrowisofs Called brasero_job_set_progress (0.519700)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  52.30% done, estimate finish Thu Jan  8 08:51:04 2009
BraseroGrowisofs Called brasero_job_set_progress (0.523000)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  52.63% done, estimate finish Thu Jan  8 08:51:04 2009
BraseroGrowisofs Called brasero_job_set_progress (0.526300)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  52.96% done, estimate finish Thu Jan  8 08:51:02 2009
BraseroGrowisofs Called brasero_job_set_progress (0.529600)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  53.30% done, estimate finish Thu Jan  8 08:51:00 2009
BraseroGrowisofs Called brasero_job_set_progress (0.533000)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  53.63% done, estimate finish Thu Jan  8 08:50:59 2009
BraseroGrowisofs Called brasero_job_set_progress (0.536300)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  53.96% done, estimate finish Thu Jan  8 08:50:57 2009
BraseroGrowisofs Called brasero_job_set_progress (0.539600)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  54.30% done, estimate finish Thu Jan  8 08:50:55 2009
BraseroGrowisofs Called brasero_job_set_progress (0.543000)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  54.63% done, estimate finish Thu Jan  8 08:50:55 2009
BraseroGrowisofs Called brasero_job_set_progress (0.546300)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  54.96% done, estimate finish Thu Jan  8 08:50:53 2009
BraseroGrowisofs Called brasero_job_set_progress (0.549600)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  55.30% done, estimate finish Thu Jan  8 08:50:51 2009
BraseroGrowisofs Called brasero_job_set_progress (0.553000)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  55.63% done, estimate finish Thu Jan  8 08:50:51 2009
BraseroGrowisofs Called brasero_job_set_progress (0.556300)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  55.96% done, estimate finish Thu Jan  8 08:50:49 2009
BraseroGrowisofs Called brasero_job_set_progress (0.559600)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  56.30% done, estimate finish Thu Jan  8 08:50:47 2009
BraseroGrowisofs Called brasero_job_set_progress (0.563000)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  56.63% done, estimate finish Thu Jan  8 08:50:47 2009
BraseroGrowisofs Called brasero_job_set_progress (0.566300)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  56.96% done, estimate finish Thu Jan  8 08:50:45 2009
BraseroGrowisofs Called brasero_job_set_progress (0.569600)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  57.30% done, estimate finish Thu Jan  8 08:50:43 2009
BraseroGrowisofs Called brasero_job_set_progress (0.573000)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  57.63% done, estimate finish Thu Jan  8 08:50:42 2009
BraseroGrowisofs Called brasero_job_set_progress (0.576300)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  57.96% done, estimate finish Thu Jan  8 08:50:41 2009
BraseroGrowisofs Called brasero_job_set_progress (0.579600)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  58.29% done, estimate finish Thu Jan  8 08:50:40 2009
BraseroGrowisofs Called brasero_job_set_progress (0.582900)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  58.63% done, estimate finish Thu Jan  8 08:50:38 2009
BraseroGrowisofs Called brasero_job_set_progress (0.586300)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  58.96% done, estimate finish Thu Jan  8 08:50:38 2009
BraseroGrowisofs Called brasero_job_set_progress (0.589600)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  59.29% done, estimate finish Thu Jan  8 08:50:36 2009
BraseroGrowisofs Called brasero_job_set_progress (0.592900)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  59.63% done, estimate finish Thu Jan  8 08:50:34 2009
BraseroGrowisofs Called brasero_job_set_progress (0.596300)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  59.96% done, estimate finish Thu Jan  8 08:50:34 2009
BraseroGrowisofs Called brasero_job_set_progress (0.599600)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  60.29% done, estimate finish Thu Jan  8 08:50:33 2009
BraseroGrowisofs Called brasero_job_set_progress (0.602900)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  60.63% done, estimate finish Thu Jan  8 08:50:31 2009
BraseroGrowisofs Called brasero_job_set_progress (0.606300)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  60.96% done, estimate finish Thu Jan  8 08:50:29 2009
BraseroGrowisofs Called brasero_job_set_progress (0.609600)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  61.29% done, estimate finish Thu Jan  8 08:50:29 2009
BraseroGrowisofs Called brasero_job_set_progress (0.612900)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  61.63% done, estimate finish Thu Jan  8 08:50:28 2009
BraseroGrowisofs Called brasero_job_set_progress (0.616300)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  61.96% done, estimate finish Thu Jan  8 08:50:26 2009
BraseroGrowisofs Called brasero_job_set_progress (0.619600)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  62.29% done, estimate finish Thu Jan  8 08:50:26 2009
BraseroGrowisofs Called brasero_job_set_progress (0.622900)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  62.62% done, estimate finish Thu Jan  8 08:50:24 2009
BraseroGrowisofs Called brasero_job_set_progress (0.626200)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  62.96% done, estimate finish Thu Jan  8 08:50:23 2009
BraseroGrowisofs Called brasero_job_set_progress (0.629600)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  63.29% done, estimate finish Thu Jan  8 08:50:21 2009
BraseroGrowisofs Called brasero_job_set_progress (0.632900)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  63.62% done, estimate finish Thu Jan  8 08:50:21 2009
BraseroGrowisofs Called brasero_job_set_progress (0.636200)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  63.96% done, estimate finish Thu Jan  8 08:50:20 2009
BraseroGrowisofs Called brasero_job_set_progress (0.639600)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  64.29% done, estimate finish Thu Jan  8 08:50:18 2009
BraseroGrowisofs Called brasero_job_set_progress (0.642900)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  64.62% done, estimate finish Thu Jan  8 08:50:17 2009
BraseroGrowisofs Called brasero_job_set_progress (0.646200)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  64.96% done, estimate finish Thu Jan  8 08:50:17 2009
BraseroGrowisofs Called brasero_job_set_progress (0.649600)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  65.29% done, estimate finish Thu Jan  8 08:50:15 2009
BraseroGrowisofs Called brasero_job_set_progress (0.652900)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  65.62% done, estimate finish Thu Jan  8 08:50:14 2009
BraseroGrowisofs Called brasero_job_set_progress (0.656200)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  65.96% done, estimate finish Thu Jan  8 08:50:12 2009
BraseroGrowisofs Called brasero_job_set_progress (0.659600)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  66.29% done, estimate finish Thu Jan  8 08:50:12 2009
BraseroGrowisofs Called brasero_job_set_progress (0.662900)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  66.62% done, estimate finish Thu Jan  8 08:50:11 2009
BraseroGrowisofs Called brasero_job_set_progress (0.666200)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  66.96% done, estimate finish Thu Jan  8 08:50:09 2009
BraseroGrowisofs Called brasero_job_set_progress (0.669600)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  67.29% done, estimate finish Thu Jan  8 08:50:08 2009
BraseroGrowisofs Called brasero_job_set_progress (0.672900)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  67.62% done, estimate finish Thu Jan  8 08:50:08 2009
BraseroGrowisofs Called brasero_job_set_progress (0.676200)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr: :-[ WRITE@LBA=f4560h failed with SK=3h/NO SEEK COMPLETE]: Input/output error
BraseroGrowisofs stderr: :-( write failed: Input/output error
BraseroGrowisofs called brasero_job_error
BraseroGrowisofs finished with an error
BraseroGrowisofs asked to stop because of an error
	error		= 1
	message	= "Unhandled error, aborting"
BraseroGrowisofs stopping
BraseroGrowisofs got killed
Session error : Unhandled error, aborting (brasero_burn_record burn.c:2524)

```

---

### Post by Julius1988 on 2009-01-08
try to remove and reinstall it or try k3b

---

### Post by leveliv on 2009-01-08
I have k3b and it does the same thing

---

### Post by albinootje on 2009-01-08
> **leveliv said:**
> I have k3b and it does the same thing

Are you using 8.04 ? 
Try adding the all_generic_ide kernel parameter before booting.

---

### Post by exploder on 2009-01-08
Installing the newer Brasero package will resolve the problem. Getdeb has what you need.

Brasero for the Intrepid release.

[http://www.getdeb.net/search.php?keywords=brasero](http://www.getdeb.net/search.php?keywords=brasero)

Brasero for the Hardy release.

[http://www.getdeb.net/search.php?search_distro_id=9&keywords=brasero](http://www.getdeb.net/search.php?search_distro_id=9&keywords=brasero)

Version 0.8.4 took care of the problems I was having, even the plugins are working properly now.

---

### Post by leveliv on 2009-01-08
hmm thanks I will try updating the client but I have a feeling it may not work but it is worth a shot. Thanks

---

### Post by editrix on 2009-01-09
There are **lots** of burning bugs in Hardy. I've got a post here [http://ubuntuforums.org/showthread.php?t=884700](http://ubuntuforums.org/showthread.php?t=884700) that lists some possible solutions.

---

