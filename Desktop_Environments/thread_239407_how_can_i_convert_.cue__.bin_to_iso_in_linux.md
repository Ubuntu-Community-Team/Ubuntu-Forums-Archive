---
title: "how can i convert .cue / .bin to iso in linux"
date: 2006-08-19
forum: Desktop Environments
---

### Post by cosmoshell on 2006-08-19
how can i convert .cue / .bin to iso in linux

---

### Post by noof on 2006-08-19
google is your friend, a search for "linux convert cue bin to iso" yielded the folling result:
[http://he.fi/bchunk/](http://he.fi/bchunk/)

apt-get install bchunk

---

### Post by Ziox on 2006-08-19
or search for it in apt:

apt-cache search convert cue bin iso

---

### Post by fakie_flip on 2006-09-04
What is the correct way to use bchunk to convert bin and cue to iso? Thanks.

---

### Post by Ziox on 2006-09-04
try it's man page:

man bchunck

---

### Post by taurus on 2006-09-04
And there is a bin2iso!!!

---

### Post by Ziox on 2006-09-04
> **taurus said:**
> And there is a bin2iso!!!

how could've I forgotten about that?  It's the one I used :p 

+1 for bin2iso =D>

---

### Post by Zackie on 2008-02-22
I have sudo apt get the bchunk and it installed but i can not find where it is to use it.. where should i look for it?:guitar:


Update****Okay i  just typed bchunk in the terminal and got this> zackie@zackie:~$ bchunk
binchunker for Unix, version 1.2.0 by Heikki Hannikainen <hessu@hes.iki.fi>
        Created with the kind help of Bob Marietta <marietrg@SLU.EDU>,
        partly based on his Pascal (Delphi) implementation.
        Support for MODE2/2352 ISO tracks thanks to input from
        Godmar Back <gback@cs.utah.edu>, Colas Nahaboo <Colas@Nahaboo.com>
        and Matthew Green <mrg@eterna.com.au>.
        Released under the GNU GPL, version 2 or later (at your option).

Usage: bchunk [-v] [-r] [-p (PSX)] [-w (wav)] [-s (swabaudio)]
         <image.bin> <image.cue> <basename>
Example: bchunk foo.bin foo.cue foo
  -v  Verbose mode
  -r  Raw mode for MODE2/2352: write all 2352 bytes from offset 0 (VCD/MPEG)
  -p  PSX mode for MODE2/2352: write 2336 bytes from offset 24
      (default MODE2/2352 mode writes 2048 bytes from offset 24)
  -w  Output audio files in WAV format
  -s  swabaudio: swap byte order in audio tracks


Not sure if i need to use bchunk this way or if there is a gui somewhere on my computer that i just don't see... and clues...?

---

### Post by graabein on 2008-03-02
See [this thread]("http://ubuntuforums.org/showthread.php?p=4438931"). Works for me.

---

### Post by kaji_arg on 2008-03-30
Wow, have you tried kiso?

Just right-click on the cue file from konqueror and Action/Kiso/Convert to ISO... wait.. and done

if you got problems with that just install all the recommended files from kiso

---

