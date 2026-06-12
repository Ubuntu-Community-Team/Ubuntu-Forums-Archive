---
title: "Brasero fails to burn DVD image"
date: 2009-04-02
forum: General Help
---

### Post by logixoul on 2009-04-02
Hi.
Ibex here.
Trying to burn a dvd image with default options in Brasero, also tried in Nautilus. I get this error log, can you help?

Checking session consistency (brasero_burn_check_session_consistency burn.c:1843)
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_set_output_size_for_current_track
BraseroChecksumImage stopping
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage output set (IMAGE) image = /tmp/brasero_tmp_X98TRU toc = nil
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_input_type
BraseroChecksumImage called brasero_job_set_current_action
BraseroChecksumImage called brasero_job_start_progress
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage Starting checksuming file /lx/bievx64sp139.iso (size = 88866816)
BraseroChecksumImage called brasero_job_get_fd_out
BraseroChecksumImage Called brasero_job_set_progress (0.004432)
BraseroChecksumImage Called brasero_job_set_progress (0.005984)
BraseroChecksumImage Called brasero_job_set_progress (0.009184)
[..snip..]
BraseroChecksumImage Called brasero_job_set_progress (0.985480)
BraseroChecksumImage Called brasero_job_set_progress (0.989128)
BraseroChecksumImage Called brasero_job_set_progress (0.995937)
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage setting new checksum (type = 0) da665ad801f78a8f7ca0e814243e7cf5 ( before)
BraseroChecksumImage finished track successfully
BraseroChecksumImage stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_set_output_size_for_current_track
BraseroLocalTrack stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack output set (IMAGE) image = /tmp/brasero_tmp_O16XRU toc = nil
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
BraseroLocalTrack no foreign URIs
BraseroLocalTrack stopping
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
  -speed=2
  -use-the-force-luke=tracksize:2140544
  -use-the-force-luke=tty
  -Z
  /dev/scd0=/lx/bievx64sp139.iso
BraseroGrowisofs launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stdout: Executing 'builtin_dd if=/lx/bievx64sp139.iso of=/dev/scd0 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous
BraseroGrowisofs stderr: /dev/scd0: engaging DVD-RW DAO upon user request...
BraseroGrowisofs stderr: : -[ PERFORM OPC failed with SK=3h/POWER CALIBRATION AREA ERROR]: Input/output error
BraseroGrowisofs stdout: HUP
BraseroGrowisofs stderr: HUP
BraseroGrowisofs process finished with status 133
BraseroGrowisofs called brasero_job_error
BraseroGrowisofs finished with an error
BraseroGrowisofs asked to stop because of an error
  error    = 0
  message  = "no message"
BraseroGrowisofs stopping
BraseroGrowisofs got killed
Session error : unknown (brasero_burn_record burn.c:2527)

---

### Post by PB_G3 on 2009-11-02
I've had the same problem in Karmic!  I think it's a corrupt ISO error...

```
Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1799)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI output set (IMAGE) image = /tmp/brasero_tmp_KSIP2U.bin toc = none
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
BraseroLocalTrack output set (IMAGE) image = /tmp/brasero_tmp_8MJP2U.bin toc = none
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack no remote URIs
BraseroLocalTrack stopping
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_flags
BraseroChecksumImage Dummy operation, skipping
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage There is a checksum already 0
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs getting varg
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_current_track
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
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs called brasero_job_get_fd_in
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs got varg:
	growisofs
	-use-the-force-luke=notray
	-use-the-force-luke=dummy
	-use-the-force-luke=4gms
	-dvd-compat
	-speed=16
	-use-the-force-luke=tracksize:2255587	
        -use-the-force-luke=tty
	-Z
	/dev/sr0=/home/angelo/CentOS-5.4-x86_64-bin-DVD/CentOS-5.4-x86_64-bin-DVD.iso
BraseroGrowisofs Launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stdout: Executing 'builtin_dd if=/home/angelo/CentOS-5.4-x86_64-bin-DVD/CentOS-5.4-x86_64-bin-DVD.iso of=/dev/sr0 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous
BraseroGrowisofs stderr: /dev/sr0: "Current Write Speed" is 16.4x1352KBps.
BraseroGrowisofs stdout:     7471104/4619442176 ( 0.2%) @1.4x, remaining 72:01 RBU 100.0% UBU   9.7%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:    38699008/4619442176 ( 0.8%) @6.8x, remaining 19:43 RBU 100.0% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:    70451200/4619442176 ( 1.5%) @6.9x, remaining 15:03 RBU 100.0% UBU  99.4%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   102662144/4619442176 ( 2.2%) @7.0x, remaining 12:27 RBU 100.0% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   135364608/4619442176 ( 2.9%) @7.1x, remaining 11:02 RBU  99.7% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   168558592/4619442176 ( 3.6%) @7.2x, remaining 10:33 RBU  98.9% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   202244096/4619442176 ( 4.4%) @7.3x, remaining 9:49 RBU  99.6% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   236421120/4619442176 ( 5.1%) @7.4x, remaining 9:16 RBU 100.0% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   271089664/4619442176 ( 5.9%) @7.5x, remaining 9:05 RBU  99.9% UBU  99.6%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   306282496/4619442176 ( 6.6%) @7.6x, remaining 8:41 RBU  99.6% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   341934080/4619442176 ( 7.4%) @7.7x, remaining 8:20 RBU  99.7% UBU  99.6%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   378077184/4619442176 ( 8.2%) @7.8x, remaining 8:13 RBU  99.8% UBU  99.6%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   414744576/4619442176 ( 9.0%) @7.9x, remaining 7:56 RBU 100.0% UBU  97.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   451870720/4619442176 ( 9.8%) @8.0x, remaining 7:41 RBU 100.0% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   489521152/4619442176 (10.6%) @8.2x, remaining 7:35 RBU  99.7% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   527630336/4619442176 (11.4%) @8.3x, remaining 7:22 RBU 100.0% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   566231040/4619442176 (12.3%) @8.4x, remaining 7:09 RBU 100.0% UBU  99.6%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   605356032/4619442176 (13.1%) @8.5x, remaining 7:04 RBU  99.9% UBU  96.2%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   644972544/4619442176 (14.0%) @8.6x, remaining 6:52 RBU  98.9% UBU  99.6%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   685047808/4619442176 (14.8%) @8.7x, remaining 6:42 RBU  99.4% UBU  99.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   725647360/4619442176 (15.7%) @8.8x, remaining 6:37 RBU  99.9% UBU  99.6%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   766705664/4619442176 (16.6%) @8.9x, remaining 6:26 RBU 100.0% UBU  99.6%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   808288256/4619442176 (17.5%) @9.0x, remaining 6:17 RBU  98.9% UBU  99.6%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   850329600/4619442176 (18.4%) @9.1x, remaining 6:12 RBU  99.9% UBU  99.6%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   892895232/4619442176 (19.3%) @9.2x, remaining 6:03 RBU  99.9% UBU  99.6%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   935952384/4619442176 (20.3%) @9.3x, remaining 5:54 RBU  99.6% UBU  98.6%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:   979468288/4619442176 (21.2%) @9.4x, remaining 5:49 RBU 100.0% UBU  99.6%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1023508480/4619442176 (22.2%) @9.5x, remaining 5:40 RBU  99.7% UBU  99.6%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1068040192/4619442176 (23.1%) @9.6x, remaining 5:32 RBU  99.8% UBU  99.6%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1113063424/4619442176 (24.1%) @9.7x, remaining 5:27 RBU  99.9% UBU  99.6%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1158545408/4619442176 (25.1%) @9.8x, remaining 5:19 RBU 100.0% UBU  99.6%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1204551680/4619442176 (26.1%) @10.0x, remaining 5:11 RBU  96.9% UBU  97.6%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1251049472/4619442176 (27.1%) @10.1x, remaining 5:06 RBU  98.5% UBU  99.6%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1298006016/4619442176 (28.1%) @10.2x, remaining 4:59 RBU  99.6% UBU  99.6%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1345454080/4619442176 (29.1%) @10.3x, remaining 4:52 RBU  99.7% UBU  99.6%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1393426432/4619442176 (30.2%) @10.4x, remaining 4:47 RBU 100.0% UBU  99.6%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1441890304/4619442176 (31.2%) @10.5x, remaining 4:39 RBU  99.7% UBU  99.6%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1490845696/4619442176 (32.3%) @10.6x, remaining 4:32 RBU  99.9% UBU  99.6%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1540259840/4619442176 (33.3%) @10.7x, remaining 4:27 RBU  99.8% UBU  99.6%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1590198272/4619442176 (34.4%) @10.8x, remaining 4:20 RBU  98.4% UBU  99.6%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1640628224/4619442176 (35.5%) @10.9x, remaining 4:14 RBU  97.3% UBU  90.7%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1691549696/4619442176 (36.6%) @11.0x, remaining 4:09 RBU  98.6% UBU  99.6%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1742962688/4619442176 (37.7%) @11.1x, remaining 4:02 RBU 100.0% UBU  99.6%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1794867200/4619442176 (38.9%) @11.2x, remaining 3:56 RBU  93.0% UBU  99.6%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1847263232/4619442176 (40.0%) @11.3x, remaining 3:51 RBU  79.9% UBU  99.6%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1900150784/4619442176 (41.1%) @11.4x, remaining 3:44 RBU  87.1% UBU  79.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  1953529856/4619442176 (42.3%) @11.6x, remaining 3:38 RBU  95.2% UBU  99.6%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2007400448/4619442176 (43.5%) @11.7x, remaining 3:33 RBU  97.2% UBU  99.6%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2061762560/4619442176 (44.6%) @11.8x, remaining 3:27 RBU  97.0% UBU  99.6%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2116648960/4619442176 (45.8%) @11.9x, remaining 3:21 RBU  99.7% UBU  87.1%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2171994112/4619442176 (47.0%) @12.0x, remaining 3:16 RBU  99.6% UBU  99.6%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2227830784/4619442176 (48.2%) @12.1x, remaining 3:10 RBU 100.0% UBU  99.6%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2284158976/4619442176 (49.4%) @12.2x, remaining 3:04 RBU  99.7% UBU  99.6%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2340978688/4619442176 (50.7%) @12.3x, remaining 2:59 RBU  99.9% UBU  86.7%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2398289920/4619442176 (51.9%) @12.4x, remaining 2:53 RBU  99.7% UBU  99.6%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2456092672/4619442176 (53.2%) @12.5x, remaining 2:47 RBU  96.4% UBU  99.6%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2514386944/4619442176 (54.4%) @12.6x, remaining 2:42 RBU  71.8% UBU  99.6%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2573172736/4619442176 (55.7%) @12.7x, remaining 2:36 RBU  77.2% UBU  88.5%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2632482816/4619442176 (57.0%) @12.8x, remaining 2:30 RBU  62.5% UBU  99.4%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2692251648/4619442176 (58.3%) @12.9x, remaining 2:26 RBU  72.6% UBU  94.2%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2752577536/4619442176 (59.6%) @13.0x, remaining 2:20 RBU  55.3% UBU  99.6%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2813329408/4619442176 (60.9%) @13.2x, remaining 2:14 RBU  70.5% UBU  75.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2874605568/4619442176 (62.2%) @13.3x, remaining 2:09 RBU  89.7% UBU  99.4%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2936340480/4619442176 (63.6%) @13.4x, remaining 2:04 RBU  99.5% UBU  94.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  2998599680/4619442176 (64.9%) @13.5x, remaining 1:58 RBU  97.8% UBU  99.4%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3061317632/4619442176 (66.3%) @13.6x, remaining 1:54 RBU 100.0% UBU  99.4%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3124559872/4619442176 (67.6%) @13.7x, remaining 1:48 RBU  95.0% UBU  99.4%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3188260864/4619442176 (69.0%) @13.8x, remaining 1:43 RBU  99.8% UBU  99.4%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3252486144/4619442176 (70.4%) @13.9x, remaining 1:38 RBU  99.8% UBU  92.7%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3317170176/4619442176 (71.8%) @14.0x, remaining 1:33 RBU  99.2% UBU  99.4%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3382378496/4619442176 (73.2%) @14.1x, remaining 1:27 RBU  96.5% UBU  99.4%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3448078336/4619442176 (74.6%) @14.2x, remaining 1:22 RBU  91.6% UBU  99.4%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3514236928/4619442176 (76.1%) @14.3x, remaining 1:17 RBU  99.4% UBU  75.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3580887040/4619442176 (77.5%) @14.4x, remaining 1:12 RBU  98.7% UBU  99.4%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3648061440/4619442176 (79.0%) @14.5x, remaining 1:07 RBU  94.9% UBU  99.4%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3715694592/4619442176 (80.4%) @14.6x, remaining 1:02 RBU  88.1% UBU  99.4%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3783852032/4619442176 (81.9%) @14.8x, remaining 0:57 RBU  52.9% UBU  69.6%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3852500992/4619442176 (83.4%) @14.9x, remaining 0:52 RBU  58.9% UBU  99.4%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3921641472/4619442176 (84.9%) @15.0x, remaining 0:47 RBU  56.3% UBU  99.4%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  3991273472/4619442176 (86.4%) @15.1x, remaining 0:42 RBU  42.6% UBU  77.4%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  4061396992/4619442176 (87.9%) @15.2x, remaining 0:37 RBU  33.3% UBU  99.4%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  4131979264/4619442176 (89.4%) @15.3x, remaining 0:32 RBU  15.4% UBU  99.4%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  4198203392/4619442176 (90.9%) @14.3x, remaining 0:28 RBU  11.0% UBU  80.8%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  4269735936/4619442176 (92.4%) @15.5x, remaining 0:23 RBU  30.7% UBU  99.4%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  4341792768/4619442176 (94.0%) @15.6x, remaining 0:18 RBU   4.7% UBU  99.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  4397826048/4619442176 (95.2%) @12.1x, remaining 0:14 RBU   9.1% UBU  12.9%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  4460609536/4619442176 (96.6%) @13.6x, remaining 0:10 RBU   3.2% UBU  82.5%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  4520214528/4619442176 (97.9%) @12.9x, remaining 0:06 RBU  11.8% UBU  63.1%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stdout:  4576346112/4619442176 (99.1%) @12.2x, remaining 0:02 RBU   6.9% UBU  51.0%
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr: /dev/sr0: flushing cache
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs stderr: /dev/sr0: updating RMA
BraseroGrowisofs stderr: /dev/sr0: closing disc
BraseroGrowisofs stderr: HUP
BraseroGrowisofs stdout: HUP
BraseroGrowisofs process finished with status 0
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs Finished successfully session
BraseroGrowisofs stopping
BraseroGrowisofs got killed
Dummy session successfully finished (brasero_burn_record_session brasero-burn.c:2251)
Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1799)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI output set (IMAGE) image = /tmp/brasero_tmp_XZM91U.bin toc = none
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
BraseroLocalTrack output set (IMAGE) image = /tmp/brasero_tmp_JUL91U.bin toc = none
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
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
BraseroChecksumImage There is a checksum already 0
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs getting varg
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_get_current_track
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
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs called brasero_job_get_fd_in
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs got varg:
	growisofs
	-use-the-force-luke=notray
	-use-the-force-luke=4gms
	-dvd-compat
	-speed=16
	-use-the-force-luke=tracksize:2255587
	-use-the-force-luke=tty
	-Z
	/dev/sr0=/home/angelo/CentOS-5.4-x86_64-bin-DVD/CentOS-5.4-x86_64-bin-DVD.iso
BraseroGrowisofs Launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stdout: Executing 'builtin_dd if=/home/angelo/CentOS-5.4-x86_64-bin-DVD/CentOS-5.4-x86_64-bin-DVD.iso of=/dev/sr0 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous
BraseroGrowisofs stderr: :-[ PERFORM OPC failed with SK=3h/POWER CALIBRATION AREA ERROR]: Input/output error
BraseroGrowisofs stderr: HUP
BraseroGrowisofs stdout: HUP
BraseroGrowisofs process finished with status 133
BraseroGrowisofs called brasero_job_error
BraseroGrowisofs finished with an error
BraseroGrowisofs asked to stop because of an error
	error		= 0
	message	= "no message"
BraseroGrowisofs stopping
BraseroGrowisofs got killed
Session error : unknown (brasero_burn_record brasero-burn.c:2769)
```

---

### Post by Dark_Stang on 2009-11-02
You may want to try a different brand of DVD. My laptop hates Sony DVDs but loves Verbatims.

---

### Post by claypole on 2009-11-22
Upgrade the firmware of your DVDRW [http://ubuntuforums.org/showthread.php?t=915674](http://ubuntuforums.org/showthread.php?t=915674)

---

