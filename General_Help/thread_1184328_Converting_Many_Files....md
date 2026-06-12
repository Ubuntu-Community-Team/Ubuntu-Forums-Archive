---
title: "Converting Many Files..."
date: 2009-06-11
forum: General Help
---

### Post by Tews on 2009-06-11
I have a very large library of archived radio podcasts that I'd like to convert to one file for each day.  Currently I have four 15-20MB files for each show.  Is there a way to convert/join them so that I only have 1 file per show?

Thanks :)

---

### Post by MaindotC on 2009-06-11
Yep you can use many different audio tools but a lot of them are just front ends to ffmpeg.  Use ffmpeg per [this thread](http://is.gd/YDkk) on joining files.

---

### Post by Megrimn on 2009-06-11
I would try using Audacity, if it can open the file type.  Not sure if it is the most appropriate method, though.

---

### Post by FakeOutdoorsman on 2009-06-11
> **Tews said:**
> I have a very large library of archived radio podcasts that I'd like to convert to one file for each day.  Currently I have four 15-20MB files for each show.  Is there a way to convert/join them so that I only have 1 file per show?

Thanks :)

What format are these files in?  Depending on the format, you may be able to join these files without re-encoding and therefore no generational loss if using lossy formats.

---

### Post by Tews on 2009-06-11
All the files are mp3 speech files, so quality is not of a concern.  I have tried lame and CAT with no luck.  I know that Im making this harder than need be, but im stumped!

---

### Post by Chronon on 2009-06-11
How about mp3wrap?

---

### Post by niteshifter on 2009-06-11
Hi,

I had this same problem a while back. From my notes:

This [site]("http://stommel.tamu.edu/~baum/linux-music.html") put me onto these tools:

mp3split - Breaks apart an mp3 file.
mp3wrap - Combine multiple mp3 files into one. Just what you need :)

which are in the Ubuntu repositores. The page I linked to has lots of useful information but to save some wading and reading you use mp3wrap like this:
```
mp3wrap outputfile.mp3 infileA.mp3 infileB.mp3 infileC.mp3 
```
where outputfile.mp3 is the file you to create, infileA,mp3 (and the rest) are the files you wish to add together. There can be N (any number) of input files. If by chance your files are sequentially numbered, it is  easier to do this:
```
mp3wrap outfile.mp3 infile*.mp3
```
this will take infile01.mp3, infile02.mp3 etc, and stick them in order into outfile.mp3

---

### Post by ActiveFrost on 2009-06-11
Joining video ( not sure about audio files ) files can be done with Mencoder :
```
mencoder -oac copy -ovc copy -idx -o output.avi video1.avi video2.avi video3.avi
```

So .. I would try :
```
mencoder -oac copy -idx -o output.mp3 sound1.mp3 sound2.mp3
```

---

### Post by andrew.46 on 2009-06-11
Hi Tews,

> **Tews said:**
> I have a very large library of archived radio podcasts that I'd like to convert to one file for each day.  Currently I have four 15-20MB files for each show.  Is there a way to convert/join them so that I only have 1 file per show?

The silent partner of the audio world in Linux: SoX can do this and it can be done multiple ways :-). *Concatenation* is the default and I tested this with 3 mp3 files:

```

andrew@skamandros~/Desktop$ **[COLOR="Purple"]sox --show-progress file_1.mp3 file_2.mp3 file_3.mp3 merged.mp3[/COLOR]**

Input File     : '**[COLOR="Purple"]file_1.mp3[/COLOR]**'
Channels       : 2
Sample Rate    : 44100
Precision      : 16-bit
Duration       : 00:02:48.65 = 7437289 samples = 12648.5 CDDA sectors
Sample Encoding: MPEG audio (layer I, II or III)
Comments       : 
Title=Is This What Everybody Wants
Artist=Cliff Martinez
Album=Solaris
Tracknumber=1
Year=2002
Genre=12

In:99.2% 00:02:47.37 [00:00:01.28] Out:7.38M [      |      ] Hd:5.6 Clip:0    
Input File     : '**[COLOR="Purple"]file_2.mp3[/COLOR]**'
Channels       : 2
Sample Rate    : 44100
Precision      : 16-bit
Duration       : 00:02:52.64 = 7613556 samples = 12948.2 CDDA sectors
Sample Encoding: MPEG audio (layer I, II or III)
Comments       : 
Title=First Sleep
Artist=Cliff Martinez
Album=Solaris
Tracknumber=2
Year=2002
Genre=12

In:99.6% 00:02:51.92 [00:00:00.72] Out:15.0M [      |      ] Hd:4.7 Clip:0    
Input File     : '**[COLOR="Purple"]file_3.mp3[/COLOR]**'
Channels       : 2
Sample Rate    : 44100
Precision      : 16-bit
Duration       : 00:01:44.75 = 4619519 samples = 7856.32 CDDA sectors
Sample Encoding: MPEG audio (layer I, II or III)
Comments       : 
Title=Can I Sit Next To You
Artist=Cliff Martinez
Album=Solaris
Tracknumber=3
Year=2002
Genre=12

In:100%  00:01:44.77 [00:00:00.00] Out:19.7M [      |      ] Hd:0.5 Clip:0    
Done.

```

With perfect results. Mind you the meta tags were all lost but this would be expected. The magic of SoX comes when you investigate the different methods of joining files and then the different effects that can be applied to the join. Plenty of material there for a long, wet weekend :-).

All the best,

Andrew

---

### Post by colau on 2009-06-11
Nice tip.
How about winff?
```

sudo aptitude install winff

```

---

### Post by andrew.46 on 2009-06-11
Hi again,

Apropos my previous suggestion of SoX I just remembered that Jaunty at least splits the SoX package up a little:

```

aandrew@skamandros:~$ **[COLOR="Purple"]apt-cache search sox[/COLOR]**
acorn-fdisk - Partition editor for Acorn/RISC OS machines
cplay - A front-end for various audio players
dclock - Digital clock for the X Window System with flexible display
grandfatherclock - a clock that tolls time acoustically
kismet - Wireless 802.11b monitoring tool
[B][COLOR="Purple"]libsox-dev - Development files for the SoX library
libsox-fmt-all - All SoX format libraries
libsox-fmt-alsa - SoX alsa format I/O library
libsox-fmt-ao - SoX Libao format I/O library
libsox-fmt-base - Minimal set of SoX format libraries
libsox-fmt-ffmpeg - SoX ffmpeg format library
libsox-fmt-mp3 - SoX MP3 format library
libsox-fmt-oss - SoX OSS format I/O library
libsox1 - SoX library of audio effects and processing[/COLOR][/B]
saydate - speaks the current date through your sound card
**[COLOR="Purple"]sox - Swiss army knife of sound processing[/COLOR]**

```

So to get full functionality you need:

```
sudo apt-get install sox libsox-fmt-all
```

and then you should be right :-).

Andrew

---

