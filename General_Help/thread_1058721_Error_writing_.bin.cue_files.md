---
title: "Error writing .bin/.cue files"
date: 2009-02-03
forum: General Help
---

### Post by Trixilver on 2009-02-03
For some odd reason I'm not able to write any of my .cue/.bin files to discs. If I simply right click on the file and select "write to disc" I get this very brief error message:

"There was an error writing to the disc"

If I open Brasero Disc Burning and try to burn it from there I get a similar error saying that the cue file "seems to be invalid", but I can also view the log.
```
Checking session consistency (brasero_burn_check_session_consistency burn.c:1843)
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_set_output_size_for_current_track
BraseroLocalTrack stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack output set (IMAGE) image = /tmp/brasero_tmp_2POYOU.bin toc = /tmp/brasero_tmp_2POYOU
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
	-v
	2
	--speed
	32
	/home/lewis/Games/psx/Team Buddies [U] [SLUS-00869]/Team Buddies [U] [SLUS-00869].cue
BraseroCdrdao launching command
BraseroCdrdao stderr: WARNING: Environment variable 'HOME' not defined - cannot read .cdrdao.
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: Cdrdao version 1.2.2 - (C) Andreas Mueller <andreas@daneb.de>
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr:   SCSI interface library - (C) Joerg Schilling
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr:   Paranoia DAE library - (C) Monty
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: 
BraseroCdrdao stderr: Check http://cdrdao.sourceforge.net/drives.html#dt for current driver tables.
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: 
BraseroCdrdao stderr: ERROR: Cannot open audio file "Team Buddies [U] [SLUS-00869].bin": No such file or directory
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao stderr: ERROR: /home/lewis/Games/psx/Team Buddies [U] [SLUS-00869]/Team Buddies [U] [SLUS-00869].cue:9: Cannot determine length of track data specification.
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_action
BraseroCdrdao called brasero_job_get_current_track
BraseroCdrdao called brasero_job_error
BraseroCdrdao finished with an error
BraseroCdrdao asked to stop because of an error
	error		= 1
	message	= "the cue file (Team Buddies [U] [SLUS-00869].cue) seems to be invalid"
BraseroCdrdao stopping
BraseroCdrdao got killed
Session error : the cue file (Team Buddies [U] [SLUS-00869].cue) seems to be invalid (brasero_burn_record burn.c:2524)
```

---

### Post by Sefianix on 2009-02-13
same problem here except with burning a toc/bin file.  but i can burn some other things like ubuntu iso files, etc. :confused:

---

### Post by aquavitae on 2009-02-13
What if you convert it to an iso first - there's a small utility you can install called bin2iso.  Its in the repos.  Then just use the command ```
bin2iso name_of_cue_file.cue
```

---

### Post by Chonnawonga on 2009-02-25
aquavitae, I don't think bin2iso is in the repos anymore, although I might be missing something. bchunk should do the same job, though.

---

### Post by aquavitae on 2009-02-26
Yes, it seems you're right.  Although a google search produces lots of results and I've got it installed in my Arch system, so I'm not sure why its not in the repos.

---

