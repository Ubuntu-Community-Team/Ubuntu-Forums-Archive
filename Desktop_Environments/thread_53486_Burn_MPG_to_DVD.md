---
title: "Burn MPG to DVD"
date: 2005-08-01
forum: Desktop Environments
---

### Post by blockme on 2005-08-01
Hi there,

sorry I already saw some posts about this topic. But I haven't got my problem solved. Most of them gave up or used wine.

What I want to do is: I recorded a movie via kaffeine (it crashed after i close it since the last upgrade... but thats another topic).
Now I simply want to get this mpg on a DVD so I can watch it with my DVD player. How can I do this? Transcode would be the thing as I read, but I am not able to install it because of dependencies....
Is there another way? Or a solution how to get transcode installed? Thanks for help!

blockme

---

### Post by kassetra on 2005-08-01
[QUOTE=blockme]Hi there,

sorry I already saw some posts about this topic. But I haven't got my problem solved. Most of them gave up or used wine.

What I want to do is: I recorded a movie via kaffeine (it crashed after i close it since the last upgrade... but thats another topic).
Now I simply want to get this mpg on a DVD so I can watch it with my DVD player. How can I do this? Transcode would be the thing as I read, but I am not able to install it because of dependencies....
Is there another way? Or a solution how to get transcode installed? Thanks for help!

blockme[/QUOTE]

If the file is in mpeg2 format already, you don't need to convert it to a dvd format with Transcode or Mencoder - you need to create the dvd image instead. (Also barring any other funkiness like low-compressed bitrates, etc.)

Here is how you create a dvd-player-readable dvd: (you'll need dvdauthor & mkisofs installed):

1. Create the dvd file structure:```
dvdauthor -o dvd -t movie.mpg
``` 


   2. Finalize the structure:```
dvdauthor -o dvd -T
``` 


 3. Create the ISO:```
mkisofs -dvd-video -o dvd.iso dvd/
``` 
 
4. Burn the iso image. (You can use your iso burning tool of choice here - I use Gnomebaker - but if you're in KDE you'll probably want to use K3B.)

As I said before, barring any funkiness, and if your mpg is a compliant mpeg2 - you'll have a dvd-player-readable dvd.  :)

(If you do have funkiness or you need to convert your mpg file to be a compliant mpeg2 - you'll have to either use transcode or mencoder.)

---

### Post by Shiven on 2005-08-01
someone is going to have a real problem about me doing this... but here is the full guide on how to convert (any) file to dvd...

its actually on the gentoo forums, so if it says the command "emerge" just replace it with apt-get install

[http://forums.gentoo.org/viewtopic-t-117709-highlight-dvd+authoring.html](http://forums.gentoo.org/viewtopic-t-117709-highlight-dvd+authoring.html)

note: ignore the note at the top as that is not relevant to ubuntu.

hopefully that will help you out...

---

### Post by blockme on 2005-09-21
[QUOTE=Shiven]someone is going to have a real problem about me doing this... but here is the full guide on how to convert (any) file to dvd...

its actually on the gentoo forums, so if it says the command "emerge" just replace it with apt-get install

[http://forums.gentoo.org/viewtopic-t-117709-highlight-dvd+authoring.html](http://forums.gentoo.org/viewtopic-t-117709-highlight-dvd+authoring.html)

note: ignore the note at the top as that is not relevant to ubuntu.

hopefully that will help you out...[/QUOTE]


thats a great guide! thanks a lot! even better than windows proggies because you can do it in batch.

my only problem left is: How to cut the movies? When I am recording movies from TV I'd like to cut them (for windows i am using skipit to remove advertisement). is there a video editing software for users? cinerella seems unstable and for profis. kino is only for camcorders?

---

### Post by crun on 2005-09-21
Wow! That Gentoo guide is great (though a bit overwhelming at first), can't wait to try it out.

---

### Post by enopepsoo on 2007-05-23
That was an awesome help!  Thanks a lot!

---

### Post by andlinux21 on 2007-05-24
man i wonder if you can take that howto and make like a script to do most of that work for you.

---

### Post by mister_p_1998 on 2007-05-24
> **blockme said:**
> thats a great guide! thanks a lot! even better than windows proggies because you can do it in batch.

my only problem left is: How to cut the movies? When I am recording movies from TV I'd like to cut them (for windows i am using skipit to remove advertisement). is there a video editing software for users? cinerella seems unstable and for profis. kino is only for camcorders?

Try ProjectX, its free

---

### Post by cyberportal on 2007-07-08
Thanks for the n00b instructions. They were really helpful!

---

### Post by tefflox on 2007-07-19
:confused:

:(

:popcorn:


thanks, kassetra --- :KS

---

### Post by vanadium on 2007-07-19
I first wanted to mention that Kassetra in my opinion posted the shortest, fastest and most efficient way to create a video DVD from a simple mpeg, thank you!

Avidemux is a graphical linear video utility (very comparable with Windows only Virtualdub) that allows you to

* Convert a range of video formats to DVD compliant mpeg files
* Cut, split, combine .... video tracks

For more elaborate DVD authoring, graphical tools become more convenient. I recently discovered DVD styler. QDVDAuthor is another graphical solution for DVD authoring, but I did not yet work with it.

---

### Post by jaffamuffin on 2007-07-19
I stuck a DIVX on a DVD in mpg2 using DeVeDe. Pretty straight forward.

---

### Post by scottvan on 2007-10-10
I tried the method given by Kassetra, but this is the output I got:

```
scott@scott-desktop:~$ sudo dvdauthor -o dvd -t Sean307to807.mpeg
Password:
DVDAuthor::dvdauthor, version 0.6.11.
Build options: gnugetopt magick iconv freetype
Send bugs to <dvdauthor-users@lists.sourceforge.net>

INFO: dvdauthor creating VTS
STAT: Picking VTS 01

STAT: Processing Sean307to807.mpeg...
STAT: VOBU 6240 at 3452MB, 1 PGCS
INFO: Video pts = 0.178 .. 3753.494
INFO: Audio[8] pts = 0.178 .. 3753.490
STAT: VOBU 6250 at 3458MB, 1 PGCS
INFO: Generating VTS with the following video attributes:
INFO: MPEG version: mpeg2
INFO: TV standard: ntsc
INFO: Aspect ratio: 4:3
INFO: Resolution: 720x480
INFO: Audio ch 0 format: mp2/2ch, 48khz 20bps

STAT: fixed 6250 VOBUS                         
scott@scott-desktop:~$ dvdauthor -o dvd -T
DVDAuthor::dvdauthor, version 0.6.11.
Build options: gnugetopt magick iconv freetype
Send bugs to <dvdauthor-users@lists.sourceforge.net>

INFO: dvdauthor creating table of contents
INFO: Scanning dvd/VIDEO_TS/VTS_01_0.IFO
Segmentation fault (core dumped)
```

the VOB files were created in the VIDEO_TS folder.  What am I doing wrong?

---

### Post by tefflox on 2007-10-10
Converting avi to mpg to dvd is not meant to be easy on Linux.  It is meant to test your 1st base mettle.  Slow down, be patient, more considerate, and you will prevail.

Next month you can take the GNU X Windowing system for a spin around the block with your Panasonic tube.

Luke, not ready are you.

---

### Post by scottvan on 2007-10-11
> **tefflox said:**
> Converting avi to mpg to dvd is not meant to be easy on Linux.  It is meant to test your 1st base mettle.  Slow down, be patient, more considerate, and you will prevail.

Next month you can take the GNU X Windowing system for a spin around the block with your Panasonic tube.

Luke, not ready are you.

Panasonic tube?  Was that meant for me?

---

### Post by tefflox on 2007-10-11
It was only a figure of speech, from experience.

Sorry if you're getting trouble making dvd iso files.  I know it can be frustrating at first.  But once you get it to your specification, it will have been worth it.

cheers

---

