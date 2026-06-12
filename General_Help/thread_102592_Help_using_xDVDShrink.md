---
title: "Help using xDVDShrink"
date: 2005-12-12
forum: General Help
---

### Post by remick182 on 2005-12-12
**I am getting an error and not quite sure what to do to correct the issue, if anything is able to be done.  This is what I get:**
[I]PROGRESS   Rip started at 09:02:34

   DVDSHrink Function                        Status    Elapsed

   Reading the chapter list                  Done!    [00:00:00]
   Ripping Title                             Done!    [00:09:58]
   Remultiplexing                            Working!Error!

   DVDShrink has failed!
   Error:
      -> mplex reported an error re-multiplexing the MPEG2!
   Command run:
      -> nice -n +19 mplex -f 8 -o /home/dustin/temp_mov//DVD_VIDEO/DVD_VIDEO.mpg /home/dustin/temp_mov//DVD_VIDEO/DVD_VIDEO.m2v /home/dustin/temp_mov//DVD_VIDEO/DVD_VIDEO.ac3 2> /home/dustin/temp_mov//DVD_VIDEO/mplexdebug.txt

   Check all your files etc. If it appears that the problem is
   ephemeral restart the script with 'dvdshrink --restart'

   End of command output
   ---------------------------------------

   INFO: [mplex] AUDIO_STATISTICS: bd
   INFO: [mplex] Audio stream length 346329600 bytes.
   INFO: [mplex] Frames         :   225475
   INFO: [mplex] BUFFERING min 67 Buf max 8131
[COLOR="Red"]**ERROR: [mplex] MUX STATUS: Frame data under-runs detected![/COLOR]

   See the log file at /home/dustin/DVD_VIDEO.log for more information.
   Exiting![/I]
**Is there anyone who is proficient with this software?**

---

### Post by Zelut on 2005-12-28
I am getting similar errors on random DVDs (some work, some don't).  Have you made any progress on this yet?  I would love some suggestions on a fix.

---

