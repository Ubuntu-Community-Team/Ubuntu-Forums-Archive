---
title: "Brasero returning unk. error burning bin/cue"
date: 2008-12-10
forum: General Help
---

### Post by Bio Leo on 2008-12-10
Using 8.04 with a Samsung (TSSTcorp) SH-S203N burner I'm suddenly having problems burning a video CD image (bin/cue) with Brasero onto a CD-RW.  A few seconds into the run it fails with an unknown error.  Here's the log;
```
Checking session consistency (brasero_burn_check_session_consistency burn.c:1714)
Inconsistent flag: you can't use flag on_the_fly (brasero_burn_check_session_consistency burn.c:1810)
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack output set (IMAGE) image = /tmp/brasero_tmp_R4S0LU.bin toc = /tmp/brasero_tmp_R4S0LU
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
BraseroLocalTrack no foreign URIs
BraseroLocalTrack stopping
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao getting varg
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao got varg:
BraseroCdrdao deactivating
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao getting varg
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_input_type
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao called brasero_job_get_device
BraseroCdrdao called brasero_job_get_flags
BraseroCdrdao called brasero_job_get_speed
BraseroCdrdao called brasero_job_get_flags
BraseroCdrdao called brasero_job_set_use_average_rate
BraseroCdrdao called brasero_job_set_current_action
BraseroCdrdao got varg:
	cdrdao
	write
	--device
	/dev/scd0
	-n
	-v
	2
	--speed
	11
	/home/leo/movie/movie2.cue
BraseroCdrdao launching command
BraseroCdrdao stderr: WARNING: Environment variable 'HOME' not defined - cannot read .cdrdao.
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: Cdrdao version 1.2.2 - (C) Andreas Mueller <andreas@daneb.de>
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr:   SCSI interface library - (C) Joerg Schilling
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr:   Paranoia DAE library - (C) Monty
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: 
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: Check http://cdrdao.sourceforge.net/drives.html#dt for current driver tables.
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: 
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: Using libscg version 'ubuntu-0.8ubuntu1'
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: 
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: /dev/scd0: TSSTcorp CDDVDW SH-S203N	Rev: SB01
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: Using driver: Generic SCSI-3/MMC - Version 2.0 (options 0x0000)
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: 
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: Starting write at speed 10...
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: Process can be aborted with QUIT signal (usually CTRL-\).
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: WARNING: No super user permission to setup real time scheduling.
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: Turning BURN-Proof on
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: Enabling JustLink.
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: ERROR: Cannot set write parameters mode page.
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: ERROR: Cannot setup write parameters for session-at-once mode.
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: ERROR: Please try to use the 'generic-mmc-raw' driver.
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: ERROR: Writing failed.
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao stderr: HUP
BraseroCdrdao process finished with status 1
BraseroCdrdao called brasero_job_error
BraseroCdrdao finished with an error
BraseroCdrdao asked to stop because of an error
	error		= 0
	message	= "no message"
BraseroCdrdao stopping
BraseroCdrdao got killed
Session error : unknown (brasero_burn_record burn.c:2273)
```
I had been burning similar disks recently with no problems and haven't (knowingly) changed any settings or hardware.  The error log mentions HOME variable not defined but 'echo "$HOME"' in terminal returns what it should.  I've burned the same image on another computer with no problems and I've tried multiple CD-RWs.  I can burn data (not from an image) and it works fine, but I can't burn any bin/cue's, I've tried Gnomebaker as well with no luck.  Thanks for any help you can provide!

---

### Post by rye_ on 2008-12-25
I have a similar problem.
bump.

---

