---
title: "MPlayer freezes when loading a DVD"
date: 2005-07-15
forum: Desktop Environments
---

### Post by SenatorK on 2005-07-15
So I followed the HOWTO posted in these forms on how to get MPlayer up and running. MPlayer works great for other videos, but I'm having a problem playing DVDs with it. When I try to load the DVD, MPlayer basically freezes. I've had the same problem with Totem as well (default install). I'm a little confused on where to  troubleshoot next, does anyone have any ideas?

I'm currently running Hoary on a Dell Inspiron 6000 with a ATI Mobility Radeon x300 / x16 card if that makes any difference.

Output from MPlayer: (Freezes right after DVD Seek!)

[[[init getch2]]]
font: Reading section: [info]
font: Reading section: [files]
RAW: /usr/local/share/mplayer/font//iso-8859-1-a.raw  3216 x 22, 256 colors
RAW: /usr/local/share/mplayer/font//iso-8859-1-b.raw  3216 x 22, 256 colors
font: Reading section: [characters]
font: Reading section: [files]
RAW: /usr/local/share/mplayer/font//osd-mplayer-a.raw  416 x 25, 256 colors
RAW: /usr/local/share/mplayer/font//osd-mplayer-b.raw  416 x 25, 256 colors
font: Reading section: [characters]
font: resampling alpha by factor 0.750 (192) DONE!
font: resampling alpha by factor 0.750 (192) DONE!
Font /usr/local/share/mplayer/font/font.desc loaded successfully! (206 chars)
Playing dvd://1.
get_path('DVDKeys') -> '/home/kevin/.mplayer/DVDKeys'
Reading disc structure, please wait...
There are 4 titles on this DVD.
There are 23 chapters in this DVD title.
There are 1 angles in this DVD title.
DVD successfully opened.
[open] audio stream: 0 audio format: ac3 (5.1) language: en aid: 128
[open] number of audio channels on disk: 1.
[open] subtitle ( sid ): 0 language: fr
[open] subtitle ( sid ): 1 language: es
[open] number of subtitles on disk: 2
DVD start cell: 0  pack: 0x0-0xF31
DVD start=0 end=1863688
s->pos=0  newpos=0  new_bufpos=0  buflen=0
DVD Seek! lba=0x0  cell=0  packs: 0x0-0xF31

---

### Post by arnieboy on 2005-07-15
try using a different video driver on gmplayer by right clicking and going to preferences. Try X11/xv etc. and let me know if u see any difference.

---

### Post by SenatorK on 2005-07-15
Nope, went through the list of drivers and still experienced the same exact behavior.

---

### Post by RyTallica898 on 2007-07-02
I too have this tragic problem. And I gander others get the same issues.

HELP....pleas....ee.....:sad:

---

### Post by kklingerman on 2008-01-19
I had this issue.  I had to install LIBDVDCSS2 from the medibuntu website ([https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)).

---

