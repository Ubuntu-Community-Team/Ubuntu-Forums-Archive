---
title: "DVD encryption errors driving me nuts!!"
date: 2005-09-07
forum: Desktop Environments
---

### Post by scronje on 2005-09-07
This has been driving me crazy for 3 days now.

I have a new installation of Ubunty Hoary, BUT with a previously used Mepis > Ubuntu home directory on  a different partition.

I am unable to play incrypted DVDs. I have deleted the .dvdcss directory in my home directory.

I have installed all the requisite software as per the Ubuntuguide. (including libdvdcss2) Whether I use Xine or Kaffeine, I get the same type of error:

[INDENT]The source seems encrypted and can't be read. Your DVD is probably crypted. According to you country laws you can or cannot install/use libdvdcss to read this disc, which you bought (Media stream scrambled / encrypted)[/INDENT] 

When reading further in that dialogue, I find several of these errors:

[INDENT]audio_decoder: error, unknown buffer type: 01060000[/INDENT] 

Here is the output of cat .xsession-errors: 

[INDENT]libdvdnav: Using dvdnav version 1.0 from [http://xine.sf.net](http://xine.sf.net)
libdvdnav: DVD Title: QQQQQ
libdvdnav: DVD Serial Number: qqqqq
libdvdnav: DVD Title (Alternative):
libdvdnav: Unable to find map file '/home/lounge/.dvdnav/QQQQQ.map'
libdvdnav: DVD disk reports itself with Region mask 0x00f60000. Regions: 1 4
Warning: more than one line!
xiTK WARNING(xitk_font_guess_error:302): font "-*-helvetica-*-i-*-*-12-*-*-*-*-*-*-*" doesn't contain charset ISO10646-1
libdvdread: Using libdvdcss version 1.2.8 for DVD access

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient

libdvdread: Get key for /VIDEO_TS/VIDEO_TS.VOB at 0x0000012d
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_0.VOB at 0x000221df
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_01_1.VOB at 0x000281a4
libdvdread: Elapsed time 0
libdvdread: Get key for /VIDEO_TS/VTS_02_0.VOB at 0x003d2e2e
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_0.VOB (0x003d2e2e)
libdvdread: Elapsed time 3
libdvdread: Get key for /VIDEO_TS/VTS_02_1.VOB at 0x003d2e32
libdvdread: Error cracking CSS key for /VIDEO_TS/VTS_02_1.VOB (0x003d2e32)!!
libdvdread: Elapsed time 0
libdvdread: Found 2 VTS's
libdvdread: Elapsed time 3[/INDENT] 

This is driving me silly. I have read all the recent posts regarding DVD playback problems, without help. 

When Ximne crashes, I find keys in the .dvdcss directory, so that seems to be OK, but why the error then. Is the audio error to blame?

I have adjusted hdparm, to no avail.

I have used this computer regularly to play DVDs with Mepis, and I had a recent install of Ubuntu that was playing things back well, but after reinstalling, I have this problem.

The only other option I can think of is to remove the /home directory, and re-install again.

Any help will be much appreciated.

---

### Post by scronje on 2005-09-07
Solved!!

Here's what I did:

Go to the .xine directory (in your home directory)

rm catalog.cache

Go to the .dvdcss directory (in your home directory)

rm all the entries in the directory of the offending movie.

Voila!!

(Crosses fingers)  ;-)

---

### Post by SpookyGhost on 2006-11-18
I have just used you solution and it solved my problem with my new DVD.

Thank You

:D

---

### Post by JImmy Bones on 2006-11-25
I have tried the same instructions but I still can't play encrypted DVDs. The error message is the same. See below results of the .xsession-errors:
Playing dvd://2.
Reading disc structure, please wait...
There are 11 titles on this DVD.
There are 5 chapters in this DVD title.
There are 1 angles in this DVD title.
DVD successfully opened.
Encrypted VOB file! Read DOCS/HTML/en/cd-dvd.html.
Encrypted VOB file! Read DOCS/HTML/en/cd-dvd.html.
Encrypted VOB file! Read DOCS/HTML/en/cd-dvd.html.
Encrypted VOB file! Read DOCS/HTML/en/cd-dvd.html.
.....
Where am I going wrong?

---

