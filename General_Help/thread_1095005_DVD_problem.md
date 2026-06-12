---
title: "DVD problem"
date: 2009-03-13
forum: General Help
---

### Post by sirkillsalot on 2009-03-13
Hello everyone, this is my first post on the Ubuntu forum. I have been hessitant to post before now because now because I would see people getting yelled at for stupid questions

Anyway, I have a problem with DVDs, I can't read any DVDs I can't burn DVDs,
I can read and write CDs no problem. I have googled and looked at forums but never really found an answer. Hopefully someone can help me

When I try to burn an iso in Brasero it says "Starting to Burn"
within 5 seconds of a window pops up saying

Error while burning:
An unknown error occured. Check your disc.

And when I go to the Error log it says:


Checking session consistency (brasero_burn_check_session_consistency burn.c:1714)
Inconsistent flag: you can't use flag on_the_fly (brasero_burn_check_session_consistency burn.c:1810)
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack stopping
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack output set (IMAGE) image = /tmp/brasero_tmp_E8JUQU toc = (null)
BraseroLocalTrack called brasero_job_get_session_output_size
BraseroLocalTrack called brasero_job_get_action
BraseroLocalTrack called brasero_job_get_current_track
BraseroLocalTrack called brasero_job_get_input_type
BraseroLocalTrack no foreign URIs
BraseroLocalTrack stopping
BraseroMd5sum called brasero_job_get_action
BraseroMd5sum called brasero_job_get_action
BraseroMd5sum deactivating
BraseroMd5sum called brasero_job_get_action
BraseroMd5sum output set (IMAGE) image = /tmp/brasero_tmp_OZRUQU toc = (null)
BraseroMd5sum called brasero_job_get_session_output_size
BraseroMd5sum called brasero_job_get_action
BraseroMd5sum called brasero_job_get_action
BraseroMd5sum called brasero_job_get_input_type
BraseroMd5sum called brasero_job_get_fd_in
BraseroMd5sum called brasero_job_get_current_track
BraseroMd5sum called brasero_job_set_current_action
BraseroMd5sum called brasero_job_start_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_set_progress
BraseroMd5sum called brasero_job_get_action
BraseroMd5sum called brasero_job_get_input_type
BraseroMd5sum called brasero_job_get_current_track
BraseroMd5sum setting new checksum 0ef3ddf68ac2b1d7b24a63ca562cc1ca ((null) before)
BraseroMd5sum finished track successfully
BraseroMd5sum stopping
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
-speed=4
-use-the-force-luke=tracksize:876013
-use-the-force-luke=tty
-Z
/dev/scd0=/home/god/Desktop/.iso's/DVL_1.5_Infectious_Disease.iso
BraseroGrowisofs launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stdout: Executing 'builtin_dd if=/home/god/Desktop/.iso's/DVL_1.5_Infectious_Disease.iso of=/dev/scd0 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous
BraseroGrowisofs stderr: /dev/scd0: engaging DVD-R DAO upon user request...
BraseroGrowisofs stderr: :-[ PERFORM OPC failed with SK=3h/ASC=73h/ACQ=03h]: Input/output error
BraseroGrowisofs stdout: HUP
BraseroGrowisofs stderr: HUP
BraseroGrowisofs process finished with status 133
BraseroGrowisofs called brasero_job_error
BraseroGrowisofs finished with an error
BraseroGrowisofs asked to stop because of an error
error = 0
message = "no message"
BraseroGrowisofs stopping
BraseroGrowisofs got killed
Session error : unknown (brasero_burn_record burn.c:2273)


In GnomeBaker I get the output of

Executing 'builtin_dd if=/home/god/Desktop/.iso's/DVL_1.5_Infectious_Disease.iso of=/dev/sr0 obs=32k seek=0'
:-[ PERFORM OPC failed with SK=3h/ASC=73h/ACQ=03h]: Input/output error


Hopefully someone will be able to help me and anyone else that may have this problem.
Thanks in advance

-Austin

---

### Post by jackflap on 2009-03-13
Sorry to hear people have been shouting at people for asking silly questions, I always felt that most of the Ubuntu community isn't like that, but I guess there are inevitably bad apples thrown in the mix.

Hm, this one's a difficult one to answer without being a dev really..

Here are a couple of things you could try to see if they can lead you to a solution-

1) Try K3b.. It's a very good and mature burning application. I've seen it succeed where brasero has fallen down before. You can install it from the package manager.

2) Boot the Jaunty alpha live cd and test burning something directly from the live cd session. It's running a newer kernel and maybe you DVD driver has been updated. Or even boot an older release, i.e. if you're on Intrepid, try Hardy. Sometimes things break.

Let us know what happens,
Alex

---

### Post by roccivic on 2009-03-13
Don't know if it will help but your try to install DVD support. Open a terminal (Applications -> Accessories -> Terminal) and type in:

```
sudo apt-get install ubuntu-restricted-extras
```

Rouslan

---

### Post by wildman4god on 2009-03-13
It sounds like a driver issue, what model is you computer how new is it? sometimes ubuntu doesn't work the greatest on the newest hardware because the devs haven't reverse engineered the drivers yet if they are proprietary.

---

