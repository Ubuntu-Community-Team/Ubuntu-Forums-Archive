---
title: "&quot;Medium error&quot; when burning a cd with Brasero"
date: 2011-02-02
forum: Desktop Environments
---

### Post by oskar.hansen on 2011-02-02
I got this "medium error" when i tried to burn a cd on my almost new-installed (and updated) Ubuntu 10.10. Last week (then ubuntu 9.10) my drive was working fine with the same type of media so i suppose that something is wrong with the setup in ubuntu 10.10?

Well, can anybody help me out of this one? thank you for helping!:KS

The logfile:
```
Checking session consistency (brasero_burn_check_session_consistency brasero-burn.c:1744)
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_set_output_size_for_current_track
BraseroBurnURI stopping
BraseroBurnURI called brasero_job_get_action
BraseroBurnURI called brasero_job_get_session_output_size
BraseroBurnURI output set (IMAGE) image = /tmp/brasero_tmp_OXC9PV.bin toc = none
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
BraseroLocalTrack output set (IMAGE) image = /tmp/brasero_tmp_0NE9PV.bin toc = none
BraseroLocalTrack called brasero_job_get_session_output_size
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
BraseroChecksumImage called brasero_job_get_flags
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_session_output_size
BraseroChecksumImage output set (IMAGE) image = /tmp/brasero_tmp_V7X8PV.bin toc = none
BraseroChecksumImage called brasero_job_get_session_output_size
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_action
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_input_type
BraseroChecksumImage called brasero_job_set_current_action
BraseroChecksumImage called brasero_job_get_fd_in
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage Starting checksuming file /home/oskar/Hentede filer/ubuntu-10.04.1-desktop-i386.iso (size = 718864384)
BraseroChecksumImage called brasero_job_get_fd_out
BraseroChecksumImage called brasero_job_get_current_track
BraseroChecksumImage Setting new checksum (type = 2) 9a95ed6f6ec38fb58c446dba1add6a08 ((null) before)
BraseroChecksumImage Finished track successfully
BraseroChecksumImage stopping
BraseroLibburn called brasero_job_get_action
BraseroLibburn called brasero_job_get_action
BraseroLibburn unsupported operation
BraseroLibburn deactivating
BraseroLibburn called brasero_job_get_action
BraseroLibburn called brasero_job_get_action
BraseroLibburn called brasero_job_get_device
BraseroLibburn Drive (/dev/sr0) init result = 1
BraseroLibburn called brasero_job_get_flags
BraseroLibburn called brasero_job_get_media
BraseroLibburn called brasero_job_get_fd_in
BraseroLibburn called brasero_job_get_tracks
BraseroLibburn Setting multi 0
BraseroLibburn Setting burnproof 1
BraseroLibburn Setting dummy 0
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn burn_drive_convert_fs_adr( /dev/sr0 )
BraseroLibburn Writing
BraseroLibburn called brasero_job_set_dangerous
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn burn_drive_is_enumerable_adr( /dev/sr0 ) is true
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn Async START UNIT succeeded after 0.1 seconds
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn Allocating buffer via mmap()
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn cd Profile= 09h , obs= 32768 , obs_pad= 0
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn TAO pre-track 01 : get_nwa(0)=1, d=0 , demand=718864384 , cap=736960512

BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn SCSI error condition on command 2Ah WRITE(10): See MMC specs: Sense Key 3 "Medium error", ASC 10 ASCQ 00
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn Libburn reported an error SCSI error on write(656,16): See MMC specs: Sense Key 3 "Medium error", ASC 10 ASCQ 00
BraseroLibburn called brasero_job_error
BraseroLibburn finished with an error
BraseroLibburn asked to stop because of an error
	error		= 1
	message	= "SCSI error on write(656,16): See MMC specs: Sense Key 3 "Medium error", ASC 10 ASCQ 00"
BraseroLibburn stopping
Session error : SCSI error on write(656,16): See MMC specs: Sense Key 3 "Medium error", ASC 10 ASCQ 00 (brasero_burn_record brasero-burn.c:2862)
```

---

### Post by Nosferax on 2011-02-06
Same thing happened to me.

Brasero issue or driver issue?

---

### Post by Zaino120 on 2011-12-13
I am using 11.04 and have the same problem, brasero starts burning but right in the last part of the process it crashes and tells me of an error. This what it tells me (taken from the log):

BraseroLibburn SCSI error condition on command 2Ah WRITE(10): See MMC specs: Sense Key 3 "Medium error", ASC 10 ASCQ 00
BraseroLibburn called brasero_job_get_session_output_size
BraseroLibburn called brasero_job_set_current_action
BraseroLibburn Libburn reported an error SCSI error on write(225280,16): See MMC specs: Sense Key 3 "Medium error", ASC 10 ASCQ 00
BraseroLibburn called brasero_job_error
BraseroLibburn finished with an error
BraseroLibburn asked to stop because of an error
    error        = 1
    message    = "SCSI error on write(225280,16): See MMC specs: Sense Key 3 "Medium error", ASC 10 ASCQ 00"
BraseroLibburn stopping
BraseroLibburn closing connection for BraseroLibburn
Session error : SCSI error on write(225280,16): See MMC specs: Sense Key 3 "Medium error", ASC 10 ASCQ 00 (brasero_burn_record brasero-burn.c:2862)

I tried this from the terminal. With DVD's the message is:

BraseroChecksumImage Setting new checksum (type = 2) 399dd723795d567295bd76809ea80d4d (91d0bfa5277f53fe09afdd8285477a87 before)
BraseroChecksumImage called brasero_job_error
BraseroChecksumImage finished with an error
BraseroChecksumImage asked to stop because of an error
    error        = 27
    message    = "Some files may be corrupted on the disc"
BraseroChecksumImage stopping
BraseroChecksumImage closing connection for BraseroChecksumImage
Session error : Some files may be corrupted on the disc (brasero_burn_record brasero-burn.c:2862)

Thanks if anyone can help

---

