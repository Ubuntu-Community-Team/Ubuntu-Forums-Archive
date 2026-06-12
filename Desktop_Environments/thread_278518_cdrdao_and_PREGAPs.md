---
title: "cdrdao and PREGAPs"
date: 2006-10-16
forum: Desktop Environments
---

### Post by cbpxy on 2006-10-16
Hi,

I'm burning a CD using cdrdao and the lovely command line.  PREGAP has stopped working, however.  For a table of contents file like this:

```
CD_DA

TRACK AUDIO
FILE "SnS-1.wav" 0:00:0 3:00:00

TRACK AUDIO
PREGAP 00:02:00
FILE "filename1.wav" 3:05:0         

```

I get the following error:
```

prompt$ cdrdao simulate --device /dev/cdrw test.toc
Cdrdao version 1.2.1 - (C) Andreas Mueller <andreas@daneb.de>
  SCSI interface library - (C) Joerg Schilling
  Paranoia DAE library - (C) Monty

Check http://cdrdao.sourceforge.net/drives.html#dt for current driver tables.

ERROR: test.toc:8: START 00:02:00 behind or at track end.

```

(It might be that it gives me an error on line 7 rather than line 8, but that's the general form of the error.)

I've been looking on the web for similar problems, but could only come up with, from 
[http://thestarport.com/Steve_Savitzky/Tools/SongInfo.pl](http://thestarport.com/Steve_Savitzky/Tools/SongInfo.pl)[/HTML]
this code snippet:
```
# PREGAP used to work; it now causes an error:
	#     START 00:02:00 behind or at track end.
	if ($track_number > 1) { 
	    print "PREGAP 0:2:0\n";
	}
	# The one in sarge still works, so copy that to /usr/local/bin.
	#print "SILENCE 0:2:0\n";
	#print "START 0:2:0\n";
```
That's in a perl script written for Debian, I think, but it gave me a clue.  I downgraded to Breezy's version of cdrdao (1.1.9, compared with Dapper's 1.2.1), and everything works again.

I'd really like to be able to get cdrdao and the PREGAPs working again, because it really is very handy.  Do you have any ideas?

I've chosen Desktop Environments because there were other cdrdao questions here.  My apologies if it is inappropriate.

Thanks in advance!

---

