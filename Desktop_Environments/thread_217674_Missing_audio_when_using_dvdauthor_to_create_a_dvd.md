---
title: "Missing audio when using dvdauthor to create a dvd"
date: 2006-07-17
forum: Desktop Environments
---

### Post by dallingham on 2006-07-17
I am trying to convert some home videos from VHS to DVD. I am using a WinTV 150 card to convert the analog video to MPEG, and then avidemux to trim the beginning and ending of the file. 

Using dvdauthor to convert a simple mpg to a dvd image, however, creates an image that displays the video correctly, but does not provide any audio. 

I'm using the simple command:

   $ dvdauthor -o dvd -x test.xml

And the test.xml file is as basic as you can get with dvdauthor.

<dvdauthor>
    <vmgm />
    <titleset>
        <titles>
            <pgc>
                <vob file="test.mpg" />
            </pgc>
        </titles>
    </titleset>
</dvdauthor>


I get no errors. The output is below:

DVDAuthor::dvdauthor, version 0.6.11.
Build options: gnugetopt magick iconv freetype
Send bugs to <dvdauthor-users@lists.sourceforge.net>

INFO: Locale=en_US.UTF-8
INFO: Converting filenames to UTF-8
INFO: dvdauthor creating VTS
STAT: Picking VTS 01

STAT: Processing test.mpg...
STAT: VOBU 160 at 94MB, 1 PGCS
INFO: Video pts = 0.178 .. 97.441
INFO: Audio[16] pts = 0.178 .. 97.113
STAT: VOBU 162 at 96MB, 1 PGCS
INFO: Generating VTS with the following video attributes:
INFO: MPEG version: mpeg2
INFO: TV standard: ntsc
INFO: Aspect ratio: 4:3
INFO: Resolution: 720x480
INFO: Audio ch 0 format: pcm/2ch, 48khz 16bps

STAT: fixed 162 VOBUS
INFO: dvdauthor creating table of contents
INFO: Scanning dvd/VIDEO_TS/VTS_01_0.IFO

The resulting image plays video fine, but no audio exists. Interestingly enough, if use mplayer to play the VIDEO_TS/VTS_01_1.VOB file, I can hear the audio.

Any suggestions as to what is happening and how to correct it?

Thanks.

---

