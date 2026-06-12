---
title: "can't mount my cd-rom... ARGGGHHH"
date: 2009-03-25
forum: General Help
---

### Post by yergeht on 2009-03-25
When I put a dvd in, the system recognizes that I have put one in, so I click on brasero and try to burn a simple movie, in dvd mode.... it goes throught all ok and I can get 100% burn, but with an error saying that it couldn't mount the cd-rom...

Log enclosed:```
Checking session consistency (brasero_burn_check_session_consistency burn.c:1843)
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
BraseroChecksumFiles Called brasero_job_set_progress (1.000000)
BraseroChecksumFiles called brasero_job_get_flags
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles called brasero_job_get_input_type
BraseroChecksumFiles called brasero_job_get_current_track
BraseroChecksumFiles Adding graft for checksum file /.checksum.md5 file:///tmp/brasero_tmp_1502QU.md5
BraseroChecksumFiles called brasero_job_add_track
BraseroChecksumFiles called brasero_job_get_action
BraseroChecksumFiles finished track successfully
BraseroChecksumFiles stopping
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
	-speed=16
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
	/tmp/brasero_tmp_RHZ1QU
	-exclude-list
	/tmp/brasero_tmp_UJZ1QU
	-print-size
BraseroGrowisofs launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stdout: Executing 'genisoimage -r -J -input-charset utf8 -graft-points -path-list /tmp/brasero_tmp_RHZ1QU -exclude-list /tmp/brasero_tmp_UJZ1QU -print-size | builtin_dd of=/dev/scd0 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous
BraseroGrowisofs stderr: Total extents scheduled to be written = 358582
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
	-speed=16
	-use-the-force-luke=tracksize:358582
	-use-the-force-luke=tty
	-Z
	/dev/scd0
	-r
	-J
	-input-charset
	utf8
	-graft-points
	-path-list
	/tmp/brasero_tmp_TZS3QU
	-exclude-list
	/tmp/brasero_tmp_ZYS3QU
	-V
	Data disc (25 Mar 09)
	-A
	Brasero-0.8.2
	-sysid
	LINUX
	-v
BraseroGrowisofs launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stderr: genisoimage 1.1.8 (Linux)
BraseroGrowisofs stdout: Executing 'genisoimage -r -J -input-charset utf8 -graft-points -path-list /tmp/brasero_tmp_TZS3QU -exclude-list /tmp/brasero_tmp_ZYS3QU -V Data disc (25 Mar 09) -A Brasero-0.8.2 -sysid LINUX -v | builtin_dd of=/dev/scd0 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous
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
BraseroGrowisofs stderr:   1.40% done, estimate finish Wed Mar 25 15:50:41 2009
BraseroGrowisofs Called brasero_job_set_progress (0.014000)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:   2.79% done, estimate finish Wed Mar 25 15:50:41 2009
BraseroGrowisofs Called brasero_job_set_progress (0.027900)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:   4.19% done, estimate finish Wed Mar 25 15:50:41 2009
BraseroGrowisofs Called brasero_job_set_progress (0.041900)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr: /dev/scd0: engaging DVD-R DAO upon user request...
BraseroGrowisofs stderr: /dev/scd0: reserving 358582 blocks
BraseroGrowisofs stderr: , warning for short DAO recording
BraseroGrowisofs stderr: /dev/scd0: "Current Write Speed" is 16.4x1352KBps.
BraseroGrowisofs stderr:   5.58% done, estimate finish Wed Mar 25 16:01:08 2009
BraseroGrowisofs Called brasero_job_set_progress (0.055800)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:   6.97% done, estimate finish Wed Mar 25 15:59:31 2009
BraseroGrowisofs Called brasero_job_set_progress (0.069700)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:   8.37% done, estimate finish Wed Mar 25 15:58:15 2009
BraseroGrowisofs Called brasero_job_set_progress (0.083700)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:   9.76% done, estimate finish Wed Mar 25 15:57:20 2009
BraseroGrowisofs Called brasero_job_set_progress (0.097600)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  11.16% done, estimate finish Wed Mar 25 15:56:39 2009
BraseroGrowisofs Called brasero_job_set_progress (0.111600)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  12.55% done, estimate finish Wed Mar 25 15:56:07 2009
BraseroGrowisofs Called brasero_job_set_progress (0.125500)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  13.94% done, estimate finish Wed Mar 25 15:55:42 2009
BraseroGrowisofs Called brasero_job_set_progress (0.139400)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  15.34% done, estimate finish Wed Mar 25 15:55:21 2009
BraseroGrowisofs Called brasero_job_set_progress (0.153400)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  16.73% done, estimate finish Wed Mar 25 15:55:03 2009
BraseroGrowisofs Called brasero_job_set_progress (0.167300)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  18.13% done, estimate finish Wed Mar 25 15:54:49 2009
BraseroGrowisofs Called brasero_job_set_progress (0.181300)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  19.52% done, estimate finish Wed Mar 25 15:54:36 2009
BraseroGrowisofs Called brasero_job_set_progress (0.195200)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  20.92% done, estimate finish Wed Mar 25 15:54:25 2009
BraseroGrowisofs Called brasero_job_set_progress (0.209200)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  22.31% done, estimate finish Wed Mar 25 15:54:16 2009
BraseroGrowisofs Called brasero_job_set_progress (0.223100)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  23.71% done, estimate finish Wed Mar 25 15:54:07 2009
BraseroGrowisofs Called brasero_job_set_progress (0.237100)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  25.10% done, estimate finish Wed Mar 25 15:54:00 2009
BraseroGrowisofs Called brasero_job_set_progress (0.251000)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  26.50% done, estimate finish Wed Mar 25 15:53:53 2009
BraseroGrowisofs Called brasero_job_set_progress (0.265000)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  27.89% done, estimate finish Wed Mar 25 15:53:47 2009
BraseroGrowisofs Called brasero_job_set_progress (0.278900)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  29.28% done, estimate finish Wed Mar 25 15:53:41 2009
BraseroGrowisofs Called brasero_job_set_progress (0.292800)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  30.68% done, estimate finish Wed Mar 25 15:53:37 2009
BraseroGrowisofs Called brasero_job_set_progress (0.306800)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  32.07% done, estimate finish Wed Mar 25 15:53:32 2009
BraseroGrowisofs Called brasero_job_set_progress (0.320700)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  33.47% done, estimate finish Wed Mar 25 15:53:31 2009
BraseroGrowisofs Called brasero_job_set_progress (0.334700)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  34.86% done, estimate finish Wed Mar 25 15:53:27 2009
BraseroGrowisofs Called brasero_job_set_progress (0.348600)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  36.25% done, estimate finish Wed Mar 25 15:53:23 2009
BraseroGrowisofs Called brasero_job_set_progress (0.362500)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  37.65% done, estimate finish Wed Mar 25 15:53:20 2009
BraseroGrowisofs Called brasero_job_set_progress (0.376500)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  39.04% done, estimate finish Wed Mar 25 15:53:17 2009
BraseroGrowisofs Called brasero_job_set_progress (0.390400)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  40.44% done, estimate finish Wed Mar 25 15:53:14 2009
BraseroGrowisofs Called brasero_job_set_progress (0.404400)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  41.83% done, estimate finish Wed Mar 25 15:53:11 2009
BraseroGrowisofs Called brasero_job_set_progress (0.418300)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  43.23% done, estimate finish Wed Mar 25 15:53:09 2009
BraseroGrowisofs Called brasero_job_set_progress (0.432300)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  44.62% done, estimate finish Wed Mar 25 15:53:06 2009
BraseroGrowisofs Called brasero_job_set_progress (0.446200)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  46.02% done, estimate finish Wed Mar 25 15:53:04 2009
BraseroGrowisofs Called brasero_job_set_progress (0.460200)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  47.41% done, estimate finish Wed Mar 25 15:53:02 2009
BraseroGrowisofs Called brasero_job_set_progress (0.474100)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  48.81% done, estimate finish Wed Mar 25 15:53:00 2009
BraseroGrowisofs Called brasero_job_set_progress (0.488100)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  50.20% done, estimate finish Wed Mar 25 15:52:58 2009
BraseroGrowisofs Called brasero_job_set_progress (0.502000)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  51.59% done, estimate finish Wed Mar 25 15:52:56 2009
BraseroGrowisofs Called brasero_job_set_progress (0.515900)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  52.99% done, estimate finish Wed Mar 25 15:52:54 2009
BraseroGrowisofs Called brasero_job_set_progress (0.529900)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  54.38% done, estimate finish Wed Mar 25 15:52:53 2009
BraseroGrowisofs Called brasero_job_set_progress (0.543800)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  55.78% done, estimate finish Wed Mar 25 15:52:51 2009
BraseroGrowisofs Called brasero_job_set_progress (0.557800)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  57.17% done, estimate finish Wed Mar 25 15:52:48 2009
BraseroGrowisofs Called brasero_job_set_progress (0.571700)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  58.56% done, estimate finish Wed Mar 25 15:52:47 2009
BraseroGrowisofs Called brasero_job_set_progress (0.585600)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  59.96% done, estimate finish Wed Mar 25 15:52:46 2009
BraseroGrowisofs Called brasero_job_set_progress (0.599600)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  61.35% done, estimate finish Wed Mar 25 15:52:44 2009
BraseroGrowisofs Called brasero_job_set_progress (0.613500)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  62.75% done, estimate finish Wed Mar 25 15:52:43 2009
BraseroGrowisofs Called brasero_job_set_progress (0.627500)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  64.14% done, estimate finish Wed Mar 25 15:52:42 2009
BraseroGrowisofs Called brasero_job_set_progress (0.641400)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  65.54% done, estimate finish Wed Mar 25 15:52:41 2009
BraseroGrowisofs Called brasero_job_set_progress (0.655400)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  66.93% done, estimate finish Wed Mar 25 15:52:40 2009
BraseroGrowisofs Called brasero_job_set_progress (0.669300)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  68.33% done, estimate finish Wed Mar 25 15:52:39 2009
BraseroGrowisofs Called brasero_job_set_progress (0.683300)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  69.72% done, estimate finish Wed Mar 25 15:52:38 2009
BraseroGrowisofs Called brasero_job_set_progress (0.697200)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  71.12% done, estimate finish Wed Mar 25 15:52:37 2009
BraseroGrowisofs Called brasero_job_set_progress (0.711200)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  72.51% done, estimate finish Wed Mar 25 15:52:36 2009
BraseroGrowisofs Called brasero_job_set_progress (0.725100)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  73.90% done, estimate finish Wed Mar 25 15:52:34 2009
BraseroGrowisofs Called brasero_job_set_progress (0.739000)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  75.30% done, estimate finish Wed Mar 25 15:52:33 2009
BraseroGrowisofs Called brasero_job_set_progress (0.753000)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  76.69% done, estimate finish Wed Mar 25 15:52:33 2009
BraseroGrowisofs Called brasero_job_set_progress (0.766900)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  78.09% done, estimate finish Wed Mar 25 15:52:33 2009
BraseroGrowisofs Called brasero_job_set_progress (0.780900)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  79.48% done, estimate finish Wed Mar 25 15:52:32 2009
BraseroGrowisofs Called brasero_job_set_progress (0.794800)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  80.87% done, estimate finish Wed Mar 25 15:52:31 2009
BraseroGrowisofs Called brasero_job_set_progress (0.808700)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  82.27% done, estimate finish Wed Mar 25 15:52:30 2009
BraseroGrowisofs Called brasero_job_set_progress (0.822700)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  83.66% done, estimate finish Wed Mar 25 15:52:29 2009
BraseroGrowisofs Called brasero_job_set_progress (0.836600)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  85.06% done, estimate finish Wed Mar 25 15:52:29 2009
BraseroGrowisofs Called brasero_job_set_progress (0.850600)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  86.45% done, estimate finish Wed Mar 25 15:52:28 2009
BraseroGrowisofs Called brasero_job_set_progress (0.864500)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  87.85% done, estimate finish Wed Mar 25 15:52:28 2009
BraseroGrowisofs Called brasero_job_set_progress (0.878500)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  89.24% done, estimate finish Wed Mar 25 15:52:27 2009
BraseroGrowisofs Called brasero_job_set_progress (0.892400)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  90.64% done, estimate finish Wed Mar 25 15:52:26 2009
BraseroGrowisofs Called brasero_job_set_progress (0.906400)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  92.03% done, estimate finish Wed Mar 25 15:52:25 2009
BraseroGrowisofs Called brasero_job_set_progress (0.920300)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  93.43% done, estimate finish Wed Mar 25 15:52:24 2009
BraseroGrowisofs Called brasero_job_set_progress (0.934300)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  94.82% done, estimate finish Wed Mar 25 15:52:24 2009
BraseroGrowisofs Called brasero_job_set_progress (0.948200)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  96.21% done, estimate finish Wed Mar 25 15:52:23 2009
BraseroGrowisofs Called brasero_job_set_progress (0.962100)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  97.61% done, estimate finish Wed Mar 25 15:52:23 2009
BraseroGrowisofs Called brasero_job_set_progress (0.976100)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr:  99.00% done, estimate finish Wed Mar 25 15:52:23 2009
BraseroGrowisofs Called brasero_job_set_progress (0.990000)
BraseroGrowisofs called brasero_job_get_current_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs called brasero_job_start_progress
BraseroGrowisofs stderr: Total translation table size: 0
BraseroGrowisofs stderr: Total rockridge attributes bytes: 360
BraseroGrowisofs stderr: Total directory bytes: 0
BraseroGrowisofs stderr: Path table size(bytes): 10
BraseroGrowisofs stderr: Done with: The File(s)                             Block(s)    358401
BraseroGrowisofs stderr: Writing:   Ending Padblock                         Start Block 358432
BraseroGrowisofs stderr: Done with: Ending Padblock                         Block(s)    150
BraseroGrowisofs stderr: Max brk space used 0
BraseroGrowisofs stderr: 358582 extents written (700 MB)
BraseroGrowisofs stderr: /dev/scd0: flushing cache
BraseroGrowisofs Called brasero_job_set_progress (1.000000)
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout: HUP
BraseroGrowisofs stderr: HUP
BraseroGrowisofs process finished with status 0
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs finished successfully session
BraseroGrowisofs stopping
BraseroGrowisofs got killed
Session error : the disc could not be mounted (max attemps reached) (brasero_burn_record burn.c:2524)
```

---

### Post by yergeht on 2009-03-25
Aren't I also suppose to be able to 'see' my cd-rom in the /dev folder?>?, I can only 'see it from the /media folder. The drive itself will play cd's , haven't tried a dvd, prolly should, but either way, I needs help... I'm trying to watch some movies :popcorn:

---

### Post by evilaim on 2009-03-25
No, you can't see the mounted media from /dev/.  The point of /media/ is so you can mount the cdrom/dvd to a mount point and manipulate/view it.

/dev/ has nothing to do with viewing the content.

Just stay in /media/

---

### Post by yergeht on 2009-03-25
que? Every where I read I see people talking about the point point for the cd-rom to be in /dev, along with the hard drives /dev/hda0 etc etc. Am I wrong in this... I don't understand, windoz has warped my brain...

Either way... I don't/can't mount my cd-rom properly, if it's any help, my dvd-drive didn't wanna burn actual dvd's in windoz ewither just, data dvd's and cd's/vcd's... strange I know... couldn't fix it in windows either... had the drive replaced, supposedly, by the manufacturer (samsung), they said nothing was wrong

---

### Post by yergeht on 2009-03-25
So a surprise note, when I just now took out the cd to test whether the files system was actually looking at the /media/cd-rom with the bleach movie file:popcorn:that I was trying to burn, so I clicked on the movie and it plays so I ejected the dvd, the system said it couldn't mount the drive(understandable) because I have the dvd in my hand and it is burned on.... strange, try it in my dvd player but doesn't wanna work in my dvd player but works in my computer...? strange...? helP?

---

