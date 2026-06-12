---
title: "Inspiron 1100 with 9.10 - CD Drive problems"
date: 2009-12-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by motleybits on 2009-12-17
I recently installed 9.10 fresh on my older (but still formidable) Inspiron 1100.  Everything works beautifully, including the USB Wi-Fi that wouldn't work in 8.04.

They only problem is that now, whenever I place a CD (e.g., the backup of data files from my 8.04 install) into the CD drive there is no way to open that drive.  The CD title displays on the Places menu, so it must be mounting, but it won't open it when selected.  In fact no file browser will open on any location while there is a CD in the drive.  If I open my Home folder, then place a CD in the drive, the file browser closes.  If the CD is there, any attempt to open a file browser will try for a bit, then give up...

I've been using Ubuntu happily for a while but I don't know all the ins-and-outs of configuration and tweaking.  Can anyone help me figure out how to fix this anomaly?  Is there an install option I should use with this machine (I don't mind installing it again if I have to)? 

Thanks!

~ Postscript ~

I got this output when trying to open Nautilus in a terminal session, while a CD was in the drive:

~~~~~~
miki@miki-laptop:~$ nautilus

(nautilus:1691): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Initializing nautilus-gdu extension

** (nautilus:1691): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:1691): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:1691): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Segmentation fault
~~~~~~

When I run the same command with the drive empty, I get the same first line, but the command succeeds:

~~~~~~
miki@miki-laptop:~$ nautilus

(nautilus:1691): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
~~~~~~

What does this mean?  Is it something I can fix somehow?

Thanks!

---

