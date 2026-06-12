---
title: "Why do Brasero fail to burn DVD?"
date: 2009-04-05
forum: General Help
---

### Post by SpinningAround on 2009-04-05
I have two files movie A and movie B, movie B are completed successfully while movie A fails with this log, would someone please explain why?

log file:
```


Checking session consistency (brasero_burn_check_session_consistency burn.c:1956)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI output set (IMAGE) image = /tmp/brasero_tmp_SA0XRU.bin toc = none
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
BraseroLocalTrack output set (IMAGE) image = /tmp/brasero_tmp_TG4XRU.bin toc = none
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
BraseroChecksumImage output set (IMAGE) image = /tmp/brasero_tmp_IO5XRU.bin toc = none
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_input_type
BraseroChecksumImage called brasero_job_set_current_action
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage Starting checksuming file /home/ubuntu/Video/movieA.img (size = 234459136)
BraseroChecksumImage called brasero_job_get_fd_out
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage Setting new checksum (type = 1) 2a562bd1a607da89643ea06f576f1f92 ( before)
BraseroChecksumImage Finished track successfully
BraseroChecksumImage stopping
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs getting varg
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_input_type
BraseroGrowisofs got varg:
BraseroGrowisofs deactivating
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
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs got varg:
	growisofs
	-use-the-force-luke=notray
	-use-the-force-luke=dao
	-dvd-compat
	-speed=3
	-use-the-force-luke=tracksize:2211634
	-use-the-force-luke=tty
	-Z
	/dev/scd0=/home/ubuntu/Video/movieA.img
BraseroGrowisofs launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stdout: Executing 'builtin_dd if=/home/ubuntu/Video/movieA.img of=/dev/scd0 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous
BraseroGrowisofs stderr: /dev/scd0: "Current Write Speed" is 4.1x1352KBps.
BraseroGrowisofs stdout:           0/4529426432 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
BraseroGrowisofs stdout:           0/4529426432 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
BraseroGrowisofs stdout:           0/4529426432 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
BraseroGrowisofs stdout:           0/4529426432 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
BraseroGrowisofs stdout:           0/4529426432 ( 0.0%) @0x, remaining ??:?? RBU 100.0% UBU   0.0%
BraseroGrowisofs stdout:     9863168/4529426432 ( 0.2%) @2.1x, remaining 175:39 RBU 100.0% UBU   3.6%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:    28409856/4529426432 ( 0.6%) @4.0x, remaining 71:17 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:    46989312/4529426432 ( 1.0%) @4.0x, remaining 47:41 RBU 100.0% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:    65536000/4529426432 ( 1.4%) @4.0x, remaining 37:27 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:    84082688/4529426432 ( 1.9%) @4.0x, remaining 32:36 RBU 100.0% UBU  98.2%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   102629376/4529426432 ( 2.3%) @4.0x, remaining 28:45 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   121176064/4529426432 ( 2.7%) @4.0x, remaining 26:04 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   139722752/4529426432 ( 3.1%) @4.0x, remaining 24:36 RBU 100.0% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   158269440/4529426432 ( 3.5%) @4.0x, remaining 23:00 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   176816128/4529426432 ( 3.9%) @4.0x, remaining 21:44 RBU 100.0% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   195362816/4529426432 ( 4.3%) @4.0x, remaining 21:04 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   213942272/4529426432 ( 4.7%) @4.0x, remaining 20:10 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   232488960/4529426432 ( 5.1%) @4.0x, remaining 19:24 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   251035648/4529426432 ( 5.5%) @4.0x, remaining 19:01 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   269582336/4529426432 ( 6.0%) @4.0x, remaining 18:26 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   288161792/4529426432 ( 6.4%) @4.0x, remaining 17:54 RBU  99.9% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   306675712/4529426432 ( 6.8%) @4.0x, remaining 17:40 RBU 100.0% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   325222400/4529426432 ( 7.2%) @4.0x, remaining 17:14 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   343769088/4529426432 ( 7.6%) @4.0x, remaining 16:50 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   362315776/4529426432 ( 8.0%) @4.0x, remaining 16:40 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   380862464/4529426432 ( 8.4%) @4.0x, remaining 16:20 RBU 100.0% UBU  98.2%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   399441920/4529426432 ( 8.8%) @4.0x, remaining 16:01 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   417988608/4529426432 ( 9.2%) @4.0x, remaining 15:54 RBU 100.0% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   436535296/4529426432 ( 9.6%) @4.0x, remaining 15:37 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   455081984/4529426432 (10.0%) @4.0x, remaining 15:22 RBU 100.0% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   473628672/4529426432 (10.5%) @4.0x, remaining 15:16 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   492208128/4529426432 (10.9%) @4.0x, remaining 15:02 RBU 100.0% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   510722048/4529426432 (11.3%) @4.0x, remaining 14:49 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   529268736/4529426432 (11.7%) @4.0x, remaining 14:44 RBU 100.0% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   547815424/4529426432 (12.1%) @4.0x, remaining 14:32 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   566394880/4529426432 (12.5%) @4.0x, remaining 14:27 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   584941568/4529426432 (12.9%) @4.0x, remaining 14:16 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   603488256/4529426432 (13.3%) @4.0x, remaining 14:05 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   616923136/4529426432 (13.6%) @2.9x, remaining 14:09 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   635469824/4529426432 (14.0%) @4.0x, remaining 13:59 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   654049280/4529426432 (14.4%) @4.0x, remaining 13:49 RBU 100.0% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   672595968/4529426432 (14.8%) @4.0x, remaining 13:45 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   691142656/4529426432 (15.3%) @4.0x, remaining 13:36 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   709689344/4529426432 (15.7%) @4.0x, remaining 13:27 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   728236032/4529426432 (16.1%) @4.0x, remaining 13:23 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   746815488/4529426432 (16.5%) @4.0x, remaining 13:15 RBU  99.9% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   765329408/4529426432 (16.9%) @4.0x, remaining 13:06 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   783876096/4529426432 (17.3%) @4.0x, remaining 13:03 RBU 100.0% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   802422784/4529426432 (17.7%) @4.0x, remaining 12:55 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   821002240/4529426432 (18.1%) @4.0x, remaining 12:47 RBU 100.0% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   839548928/4529426432 (18.5%) @4.0x, remaining 12:44 RBU 100.0% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   858095616/4529426432 (18.9%) @4.0x, remaining 12:37 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   876642304/4529426432 (19.4%) @4.0x, remaining 12:30 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   895188992/4529426432 (19.8%) @4.0x, remaining 12:26 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   913735680/4529426432 (20.2%) @4.0x, remaining 12:19 RBU 100.0% UBU  99.6%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   932282368/4529426432 (20.6%) @4.0x, remaining 12:13 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   950829056/4529426432 (21.0%) @4.0x, remaining 12:10 RBU 100.0% UBU  95.3%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   969375744/4529426432 (21.4%) @4.0x, remaining 12:03 RBU 100.0% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   987955200/4529426432 (21.8%) @4.0x, remaining 11:56 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1006501888/4529426432 (22.2%) @4.0x, remaining 11:54 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1025048576/4529426432 (22.6%) @4.0x, remaining 11:47 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1043628032/4529426432 (23.0%) @4.0x, remaining 11:41 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1062174720/4529426432 (23.5%) @4.0x, remaining 11:38 RBU 100.0% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1080721408/4529426432 (23.9%) @4.0x, remaining 11:32 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1099268096/4529426432 (24.3%) @4.0x, remaining 11:26 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1117814784/4529426432 (24.7%) @4.0x, remaining 11:23 RBU 100.0% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1136394240/4529426432 (25.1%) @4.0x, remaining 11:17 RBU  99.9% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1149370368/4529426432 (25.4%) @2.8x, remaining 11:16 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1167917056/4529426432 (25.8%) @4.0x, remaining 11:13 RBU 100.0% UBU  98.2%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1186463744/4529426432 (26.2%) @4.0x, remaining 11:07 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1205043200/4529426432 (26.6%) @4.0x, remaining 11:02 RBU  99.9% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1223557120/4529426432 (27.0%) @4.0x, remaining 10:59 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1242103808/4529426432 (27.4%) @4.0x, remaining 10:53 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1260650496/4529426432 (27.8%) @4.0x, remaining 10:48 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1279197184/4529426432 (28.2%) @4.0x, remaining 10:45 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1297776640/4529426432 (28.7%) @4.0x, remaining 10:39 RBU  99.9% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1316323328/4529426432 (29.1%) @4.0x, remaining 10:34 RBU 100.0% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1334870016/4529426432 (29.5%) @4.0x, remaining 10:31 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1353416704/4529426432 (29.9%) @4.0x, remaining 10:26 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1371963392/4529426432 (30.3%) @4.0x, remaining 10:21 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1390510080/4529426432 (30.7%) @4.0x, remaining 10:18 RBU 100.0% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1409056768/4529426432 (31.1%) @4.0x, remaining 10:13 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1427603456/4529426432 (31.5%) @4.0x, remaining 10:10 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1446150144/4529426432 (31.9%) @4.0x, remaining 10:05 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1464729600/4529426432 (32.3%) @4.0x, remaining 10:00 RBU 100.0% UBU  98.2%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1483276288/4529426432 (32.7%) @4.0x, remaining 9:57 RBU 100.0% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1501822976/4529426432 (33.2%) @4.0x, remaining 9:52 RBU 100.0% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1520369664/4529426432 (33.6%) @4.0x, remaining 9:47 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1538916352/4529426432 (34.0%) @4.0x, remaining 9:44 RBU 100.0% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1557495808/4529426432 (34.4%) @4.0x, remaining 9:40 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1576009728/4529426432 (34.8%) @4.0x, remaining 9:35 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1594556416/4529426432 (35.2%) @4.0x, remaining 9:32 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1613103104/4529426432 (35.6%) @4.0x, remaining 9:27 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1631682560/4529426432 (36.0%) @4.0x, remaining 9:22 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1650229248/4529426432 (36.4%) @4.0x, remaining 9:20 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1668775936/4529426432 (36.8%) @4.0x, remaining 9:15 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1681326080/4529426432 (37.1%) @2.7x, remaining 9:13 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1699872768/4529426432 (37.5%) @4.0x, remaining 9:10 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1718419456/4529426432 (37.9%) @4.0x, remaining 9:06 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1736998912/4529426432 (38.3%) @4.0x, remaining 9:01 RBU  99.9% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1755512832/4529426432 (38.8%) @4.0x, remaining 8:58 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1774092288/4529426432 (39.2%) @4.0x, remaining 8:54 RBU  99.9% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1792606208/4529426432 (39.6%) @4.0x, remaining 8:49 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1811152896/4529426432 (40.0%) @4.0x, remaining 8:46 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1829732352/4529426432 (40.4%) @4.0x, remaining 8:42 RBU  99.9% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1848279040/4529426432 (40.8%) @4.0x, remaining 8:37 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1866825728/4529426432 (41.2%) @4.0x, remaining 8:34 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1885372416/4529426432 (41.6%) @4.0x, remaining 8:30 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1903919104/4529426432 (42.0%) @4.0x, remaining 8:26 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1922465792/4529426432 (42.4%) @4.0x, remaining 8:23 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1941012480/4529426432 (42.9%) @4.0x, remaining 8:18 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1959559168/4529426432 (43.3%) @4.0x, remaining 8:14 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1978105856/4529426432 (43.7%) @4.0x, remaining 8:11 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1996685312/4529426432 (44.1%) @4.0x, remaining 8:07 RBU  99.9% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2015232000/4529426432 (44.5%) @4.0x, remaining 8:02 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2033778688/4529426432 (44.9%) @4.0x, remaining 7:59 RBU 100.0% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2052325376/4529426432 (45.3%) @4.0x, remaining 7:55 RBU 100.0% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2070904832/4529426432 (45.7%) @4.0x, remaining 7:51 RBU  99.9% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2089418752/4529426432 (46.1%) @4.0x, remaining 7:48 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2107965440/4529426432 (46.5%) @4.0x, remaining 7:44 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2126512128/4529426432 (46.9%) @4.0x, remaining 7:39 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2145058816/4529426432 (47.4%) @4.0x, remaining 7:36 RBU 100.0% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2163638272/4529426432 (47.8%) @4.0x, remaining 7:32 RBU 100.0% UBU  99.1%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2182184960/4529426432 (48.2%) @4.0x, remaining 7:28 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2200731648/4529426432 (48.6%) @4.0x, remaining 7:25 RBU 100.0% UBU  98.2%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2215542784/4529426432 (48.9%) @3.2x, remaining 7:22 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2231435264/4529426432 (49.3%) @3.4x, remaining 7:19 RBU 100.0% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2249981952/4529426432 (49.7%) @4.0x, remaining 7:16 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2268528640/4529426432 (50.1%) @4.0x, remaining 7:12 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2287075328/4529426432 (50.5%) @4.0x, remaining 7:08 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2305622016/4529426432 (50.9%) @4.0x, remaining 7:05 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2324168704/4529426432 (51.3%) @4.0x, remaining 7:01 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2342715392/4529426432 (51.7%) @4.0x, remaining 6:58 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2361294848/4529426432 (52.1%) @4.0x, remaining 6:54 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2379841536/4529426432 (52.5%) @4.0x, remaining 6:50 RBU 100.0% UBU  98.2%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2398388224/4529426432 (53.0%) @4.0x, remaining 6:46 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2416934912/4529426432 (53.4%) @4.0x, remaining 6:42 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2435514368/4529426432 (53.8%) @4.0x, remaining 6:38 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2454028288/4529426432 (54.2%) @4.0x, remaining 6:35 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2472574976/4529426432 (54.6%) @4.0x, remaining 6:31 RBU 100.0% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2491121664/4529426432 (55.0%) @4.0x, remaining 6:27 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2509701120/4529426432 (55.4%) @4.0x, remaining 6:24 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2528247808/4529426432 (55.8%) @4.0x, remaining 6:20 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2546794496/4529426432 (56.2%) @4.0x, remaining 6:16 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2565341184/4529426432 (56.6%) @4.0x, remaining 6:13 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2583920640/4529426432 (57.0%) @4.0x, remaining 6:09 RBU 100.0% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2602434560/4529426432 (57.5%) @4.0x, remaining 6:05 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2620981248/4529426432 (57.9%) @4.0x, remaining 6:02 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2639560704/4529426432 (58.3%) @4.0x, remaining 5:58 RBU  99.9% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2658074624/4529426432 (58.7%) @4.0x, remaining 5:54 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2676654080/4529426432 (59.1%) @4.0x, remaining 5:51 RBU 100.0% UBU  95.3%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2695200768/4529426432 (59.5%) @4.0x, remaining 5:47 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2713780224/4529426432 (59.9%) @4.0x, remaining 5:43 RBU  99.9% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2732294144/4529426432 (60.3%) @4.0x, remaining 5:40 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2750873600/4529426432 (60.7%) @4.0x, remaining 5:36 RBU  99.9% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2762702848/4529426432 (61.0%) @2.6x, remaining 5:35 RBU 100.0% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2781249536/4529426432 (61.4%) @4.0x, remaining 5:31 RBU 100.0% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2799796224/4529426432 (61.8%) @4.0x, remaining 5:28 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2818375680/4529426432 (62.2%) @4.0x, remaining 5:24 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2836922368/4529426432 (62.6%) @4.0x, remaining 5:20 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2855469056/4529426432 (63.0%) @4.0x, remaining 5:17 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2874015744/4529426432 (63.5%) @4.0x, remaining 5:13 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2892562432/4529426432 (63.9%) @4.0x, remaining 5:10 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2911109120/4529426432 (64.3%) @4.0x, remaining 5:06 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2929688576/4529426432 (64.7%) @4.0x, remaining 5:02 RBU  99.9% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2948202496/4529426432 (65.1%) @4.0x, remaining 4:59 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2966781952/4529426432 (65.5%) @4.0x, remaining 4:55 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2985328640/4529426432 (65.9%) @4.0x, remaining 4:51 RBU  99.9% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3003875328/4529426432 (66.3%) @4.0x, remaining 4:48 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3022422016/4529426432 (66.7%) @4.0x, remaining 4:44 RBU 100.0% UBU  95.3%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3040968704/4529426432 (67.1%) @4.0x, remaining 4:40 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3059548160/4529426432 (67.5%) @4.0x, remaining 4:37 RBU  99.9% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3078062080/4529426432 (68.0%) @4.0x, remaining 4:33 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3096608768/4529426432 (68.4%) @4.0x, remaining 4:30 RBU 100.0% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3115155456/4529426432 (68.8%) @4.0x, remaining 4:26 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3133734912/4529426432 (69.2%) @4.0x, remaining 4:23 RBU 100.0% UBU  98.2%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3152281600/4529426432 (69.6%) @4.0x, remaining 4:19 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3170828288/4529426432 (70.0%) @4.0x, remaining 4:16 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3189407744/4529426432 (70.4%) @4.0x, remaining 4:12 RBU  99.9% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3207921664/4529426432 (70.8%) @4.0x, remaining 4:08 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3226468352/4529426432 (71.2%) @4.0x, remaining 4:05 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3245015040/4529426432 (71.6%) @4.0x, remaining 4:01 RBU 100.0% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3263561728/4529426432 (72.1%) @4.0x, remaining 3:58 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3282141184/4529426432 (72.5%) @4.0x, remaining 3:54 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3293642752/4529426432 (72.7%) @2.5x, remaining 3:53 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3312189440/4529426432 (73.1%) @4.0x, remaining 3:49 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3330768896/4529426432 (73.5%) @4.0x, remaining 3:46 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3349315584/4529426432 (73.9%) @4.0x, remaining 3:42 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3367862272/4529426432 (74.4%) @4.0x, remaining 3:39 RBU  98.8% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3386408960/4529426432 (74.8%) @4.0x, remaining 3:35 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3404955648/4529426432 (75.2%) @4.0x, remaining 3:31 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3423535104/4529426432 (75.6%) @4.0x, remaining 3:28 RBU  99.9% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3442049024/4529426432 (76.0%) @4.0x, remaining 3:24 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3460595712/4529426432 (76.4%) @4.0x, remaining 3:21 RBU 100.0% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3479175168/4529426432 (76.8%) @4.0x, remaining 3:17 RBU  99.9% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3497721856/4529426432 (77.2%) @4.0x, remaining 3:14 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3516268544/4529426432 (77.6%) @4.0x, remaining 3:10 RBU 100.0% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3534815232/4529426432 (78.0%) @4.0x, remaining 3:07 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3553361920/4529426432 (78.5%) @4.0x, remaining 3:03 RBU 100.0% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3571908608/4529426432 (78.9%) @4.0x, remaining 2:59 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3590455296/4529426432 (79.3%) @4.0x, remaining 2:56 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3609001984/4529426432 (79.7%) @4.0x, remaining 2:52 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3627548672/4529426432 (80.1%) @4.0x, remaining 2:49 RBU 100.0% UBU  95.5%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3646128128/4529426432 (80.5%) @4.0x, remaining 2:45 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3664674816/4529426432 (80.9%) @4.0x, remaining 2:42 RBU 100.0% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3683221504/4529426432 (81.3%) @4.0x, remaining 2:38 RBU 100.0% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3701768192/4529426432 (81.7%) @4.0x, remaining 2:35 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3720347648/4529426432 (82.1%) @4.0x, remaining 2:31 RBU  99.9% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3738861568/4529426432 (82.5%) @4.0x, remaining 2:28 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3757408256/4529426432 (83.0%) @4.0x, remaining 2:24 RBU 100.0% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3775954944/4529426432 (83.4%) @4.0x, remaining 2:21 RBU 100.0% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3794534400/4529426432 (83.8%) @4.0x, remaining 2:17 RBU 100.0% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3813081088/4529426432 (84.2%) @4.0x, remaining 2:14 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3826155520/4529426432 (84.5%) @2.8x, remaining 2:11 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3842703360/4529426432 (84.8%) @3.6x, remaining 2:08 RBU 100.0% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3861282816/4529426432 (85.2%) @4.0x, remaining 2:05 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3879829504/4529426432 (85.7%) @4.0x, remaining 2:01 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3898376192/4529426432 (86.1%) @4.0x, remaining 1:58 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3916922880/4529426432 (86.5%) @4.0x, remaining 1:54 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3935469568/4529426432 (86.9%) @4.0x, remaining 1:51 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3954016256/4529426432 (87.3%) @4.0x, remaining 1:47 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3972562944/4529426432 (87.7%) @4.0x, remaining 1:44 RBU 100.0% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3991109632/4529426432 (88.1%) @4.0x, remaining 1:40 RBU 100.0% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  4009689088/4529426432 (88.5%) @4.0x, remaining 1:37 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  4028235776/4529426432 (88.9%) @4.0x, remaining 1:33 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  4046782464/4529426432 (89.3%) @4.0x, remaining 1:30 RBU 100.0% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  4065329152/4529426432 (89.8%) @4.0x, remaining 1:26 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  4083875840/4529426432 (90.2%) @4.0x, remaining 1:23 RBU 100.0% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  4102422528/4529426432 (90.6%) @4.0x, remaining 1:19 RBU 100.0% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  4120969216/4529426432 (91.0%) @4.0x, remaining 1:16 RBU 100.0% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  4139515904/4529426432 (91.4%) @4.0x, remaining 1:12 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  4158095360/4529426432 (91.8%) @4.0x, remaining 1:09 RBU  99.9% UBU  98.2%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  4176642048/4529426432 (92.2%) @4.0x, remaining 1:06 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  4195188736/4529426432 (92.6%) @4.0x, remaining 1:02 RBU 100.0% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  4213735424/4529426432 (93.0%) @4.0x, remaining 0:59 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  4232314880/4529426432 (93.4%) @4.0x, remaining 0:55 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  4250828800/4529426432 (93.8%) @4.0x, remaining 0:52 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  4269375488/4529426432 (94.3%) @4.0x, remaining 0:48 RBU 100.0% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  4287922176/4529426432 (94.7%) @4.0x, remaining 0:45 RBU 100.0% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  4306501632/4529426432 (95.1%) @4.0x, remaining 0:41 RBU  99.9% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  4325048320/4529426432 (95.5%) @4.0x, remaining 0:38 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  4343595008/4529426432 (95.9%) @4.0x, remaining 0:34 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  4362141696/4529426432 (96.3%) @4.0x, remaining 0:31 RBU 100.0% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  4373118976/4529426432 (96.5%) @2.4x, remaining 0:29 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  4391665664/4529426432 (97.0%) @4.0x, remaining 0:25 RBU 100.0% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  4410245120/4529426432 (97.4%) @4.0x, remaining 0:22 RBU  99.9% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  4428759040/4529426432 (97.8%) @4.0x, remaining 0:18 RBU 100.0% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  4447338496/4529426432 (98.2%) @4.0x, remaining 0:15 RBU 100.0% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  4465852416/4529426432 (98.6%) @4.0x, remaining 0:11 RBU 100.0% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  4484399104/4529426432 (99.0%) @4.0x, remaining 0:08 RBU 100.0% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  4502978560/4529426432 (99.4%) @4.0x, remaining 0:04 RBU  78.9% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  4521525248/4529426432 (99.8%) @4.0x, remaining 0:01 RBU  23.6% UBU 100.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr: /dev/scd0: flushing cache
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr: /dev/scd0: closing track
BraseroGrowisofs stderr: /dev/scd0: closing disc
BraseroGrowisofs stderr: HUP
BraseroGrowisofs stdout: HUP
BraseroGrowisofs process finished with status 0
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs finished successfully session
BraseroGrowisofs stopping
BraseroGrowisofs got killed
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_flags
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage creating input
BraseroChecksumImage called brasero_job_get_action
BraseroReadom called brasero_job_get_action
BraseroReadom linked to BraseroChecksumImage
BraseroReadom getting varg
BraseroReadom called brasero_job_get_action
BraseroReadom called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_current_track
BraseroReadom called brasero_job_get_output_type
BraseroReadom called brasero_job_get_current_track
BraseroReadom called brasero_job_get_output_type
BraseroChecksumImage called brasero_job_set_current_action
BraseroReadom reading last track from sector -1 to -2
BraseroChecksumImage called brasero_job_get_current_track
BraseroReadom called brasero_job_get_fd_out
BraseroChecksumImage called brasero_job_get_fd_in
BraseroReadom called brasero_job_set_use_average_rate
BraseroReadom got varg:
	readom
	dev=/dev/scd0
	-nocorr
	-noerror
	-sectors=-1--2
BraseroChecksumImage Starting checksum generation live (size = -1)
	-f=-
BraseroChecksumImage called brasero_job_set_nonblocking
BraseroReadom launching command
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_get_fd_out
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_get_fd_out
BraseroReadom stderr: Read  speed: 16620 kB/s (CD  94x, DVD 12x).
BraseroReadom stderr: Write speed: 11080 kB/s (CD  62x, DVD  8x).
BraseroReadom stderr: Capacity: 2211648 Blocks = 4423296 kBytes = 4319 MBytes = 4529 prMB
BraseroReadom called brasero_job_set_current_action
BraseroReadom stderr: Sectorsize: 2048 Bytes
BraseroReadom stderr: Copy from SCSI (5,0,0) disk to file '-'
BraseroReadom stderr: end:        -2
BraseroReadom stderr: addr:       -1
BraseroReadom called brasero_job_get_output_type
BraseroReadom stderr: Time total: 0.010sec
BraseroReadom stderr: Read 0.00 kB at 0.0 kB/sec.
BraseroReadom stderr: HUP
BraseroReadom process finished with status 0
BraseroReadom called brasero_job_get_fd_out
BraseroReadom Finished track successfully
BraseroReadom got killed
BraseroReadom disconnecting BraseroReadom from BraseroChecksumImage
BraseroReadom deactivating
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage Setting new checksum (type = 1) d41d8cd98f00b204e9800998ecf8427e (2a562bd1a607da89643ea06f576f1f92 before)
BraseroChecksumImage called brasero_job_error
BraseroChecksumImage finished with an error
BraseroChecksumImage asked to stop because of an error
	error		= 24
	message	= "Vissa filer kan vara skadade på skivan"
BraseroChecksumImage stopping
BraseroChecksumImage closing connection for BraseroChecksumImage
Session error : Vissa filer kan vara skadade på skivan (brasero_burn_record burn.c:2650)

```

---

