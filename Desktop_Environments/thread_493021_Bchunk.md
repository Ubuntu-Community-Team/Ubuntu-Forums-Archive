---
title: "Bchunk"
date: 2007-07-05
forum: Desktop Environments
---

### Post by xcryinginrainxx on 2007-07-05
I have this file called 1.bin that I want to convert to an iso.

How do I convert it with Bchunk?

I mean I looked through the forums and I Googled it and I keep finding different commands, and i'm getting confused.

---

### Post by xcryinginrainxx on 2007-07-05
Sorry.

I really need help with this.

---

### Post by hikaricore on 2007-07-05
As you can see below the format for bchunk is:

*bchunk [options] <image.bin> <image.cue> <basename>*

options: if needed
image.bin: the name of the bin file
image.cue: the name of the cue file for the bin file
basename: the name for the iso output without the extention.

So if I wanted to convert my cd.bin/cd.cue files to an iso image with verbose terminal output I would run:

```
bchunk -v cd.bin cd.cue cd
```

---

For more info on an application the man pages are usually the best starting point.  Example:

```
man bchunk
```

I'll save you the trouble this time:

> BCHUNK(1)                                                            BCHUNK(1)



NAME
       bchunk - CD image format conversion from bin/cue to iso/cdr

SYNOPSIS
       bchunk [-v] [-p] [-r] [-w] [-s] <image.bin> <image.cue> <basename>

DESCRIPTION
       bchunk converts a CD image in a ".bin / .cue" format (sometimes ".raw /
       .cue") to a set of .iso and .cdr tracks.

       The bin/cue format is used by some non-Unix cd-writing software, but is
       not supported on most other cd-writing programs.

       image.bin  is  the raw cd image file. image.cue is the track index file
       containing track types and offsets.  basename is used for the beginning
       part of the created track files.

       The  produced  .iso  track  contains  an  ISO file system, which can be
       mounted through a loop device on Linux systems, or written  on  a  CD-R
       using  cdrecord.   The  .cdr  tracks are in the native CD audio format.
       They can be either written on a CD-R using  cdrecord  -audio,  or  con&#8208;
       verted to WAV (or any other sound format for that matter) using sox.

       It  is  advisable  to  edit  the .cue file to either MODE2/2352/2048 or
       MODE2/2352/2324 depending on whether an ISO  filesystem  or  a  VCD  is
       desired, respectively.  The format itself does not contain this feature
       and in an ambiguous case it can only guess.

OPTIONS
       -v        Makes binchunker print some more unnecessary messages,  which
                 should not be of interest for anyone.

       -w        Makes binchunker write audio tracks in WAV format.

       -s        Makes  binchunker  swap  byte  order  in the samples of audio
                 tracks.

       -p        Makes binchunker go into PSX  mode  and  truncate  MODE2/2352
                 tracks to 2336 bytes at offset 0 instead of normal 2048 bytes
                 at offset 24.

       -r        Makes binchunker output MODE2/2352 tracks in raw format, from
                 offset 0 for 2352 bytes. Good for MPEG/VCD.

FILES
       image.bin
            Raw CD image file

       image.cue
            TOC (Track index, Table Of Contents) file

       *.iso
            Tracks in ISO9660 CD filesystem format. Can be either written on a
            CD-R using cdrecord, or mounted  (on  Linux  platforms  at  least)
            through   a   loop   device   (&#8217;mount   track.iso   /mnt/cdrom  -o
            loop=/dev/loop0,blocksize=1024&#8217;).

       *.cdr
            Audio tracks in native CD audio format. They can be either written
            on  a  CD-R  using  &#8217;cdrecord -audio&#8217;, or converted to WAV (or any
            other sound format for that  matter)  using  sox  (&#8217;sox  track.cdr
            track.wav&#8217;).

       *.wav
            Audio tracks in WAV format.

SEE ALSO
       cdrecord(1), mkisofs(8), sox(1), cdrdao(1)

AUTHORS
       Heikki Hannikainen <hessu@hes.iki.fi>
       Bob Marietta <marietrg@SLU.EDU>
       Colas Nahaboo <Colas@Nahaboo.com>
       Godmar Back <gback@cs.utah.edu>
       Matthew Green <mrg@eterna.com.au>



Heikki Hannikainen            v1.2.0 29 Jun 2004                     BCHUNK(1)

---

### Post by xcryinginrainxx on 2007-07-06
Thanks so much.

Now I have to mount it, and I tried with this file called 'ATHF2.iso' that's on my desktop.

john@john-desktop:~$ sudo mount -t iso9660 -o ro,loop ~/Desktop/ATHF02.iso /media/cdrom0
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

john@john-desktop:~$ 

What's wrong?

---

### Post by xcryinginrainxx on 2007-07-06
Sorry again.

Please help.

---

### Post by graabein on 2008-03-01
I also need to do this. I have a bin file I want to mount as cdrom but I don't have the cue file. 

Step 1: Convert the bin file to iso.

Step 2: Mount the iso file.

---

### Post by graabein on 2008-03-02
OK I googled some more and came up with [this blog post]("http://linuxexpert.wordpress.com/2007/08/25/how-to-convert-bin-to-iso-image-whithout-having-cue-file/"). I'll try it out.

---

