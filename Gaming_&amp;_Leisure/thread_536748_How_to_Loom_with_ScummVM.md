---
title: "How to: Loom with ScummVM"
date: 2007-08-28
forum: Gaming &amp; Leisure
---

### Post by ibbuntu on 2007-08-28
I don't know if there'll be anyone else out there that would benefit from this, but I spent a few hours banging my head against the wall trying to make this work so I thought I'd write a 'howto'.

So, I have the Loom CD and I wanted to play it again. Here are the steps I needed to get it to work with Ubuntu:
[LIST=1]
[*]Install ScummVM:
```
sudo apt-get install scummvm
```
or of course you can go to System->Administration->Synaptic and install it from there. I think it's in the multiverse repositories, so make sure you have those enabled.
[*]Insert your Loom CD into your drive, and run scummvm.
[*]In ScummVM click on 'Add Game...' and navigate to /cdrom and choose that directory.
[*]Press Start, now if you're lucky the game will start and you'll have sound from the CD and you can play to your heart's content. However if you're unlucky, like me, then you'll need to do a little bit more.
[*]Copy the CD's contents to a directory of your choosing, I used ~/Loom.
[*]Now in that directory, rip the audio tracks from the CD:
```
cdparanoia -B "2-"
```
This will create a file called 'track02.cdda.wav'.
[*]Now convert this to MP3:
```
sudo apt-get install lame
lame -t -q 9 -b 96 track02.cdda.wav track1.mp3

```
It is important that the file is called track1.mp3, so that the game can find it.
[*]Now in ScummVM use 'Add Game...' and choose the directory you copied the files into, i.e. ~/Loom, and press Start. You should now have sound. Enjoy.
[/LIST]

There are many other games you can run with ScummVM, see [www.scummvm.org](www.scummvm.org) for details.

---

### Post by ddrichardson on 2007-08-29
Nice Howto

UAResolved

---

### Post by ibbuntu on 2007-08-29
Thanks, it's my first one. Hopefully I'll be able to contribute more in time.

---

### Post by BoyOfDestiny on 2007-08-29
> **ibbuntu said:**
> I don't know if there'll be anyone else out there that would benefit from this, but I spent a few hours banging my head against the wall trying to make this work so I thought I'd write a 'howto'.

So, I have the Loom CD and I wanted to play it again. Here are the steps I needed to get it to work with Ubuntu:
[LIST=1]
[*]Install ScummVM:
```
sudo apt-get install scummvm
```
or of course you can go to System->Administration->Synaptic and install it from there. I think it's in the multiverse repositories, so make sure you have those enabled.
[*]Insert your Loom CD into your drive, and run scummvm.
[*]In ScummVM click on 'Add Game...' and navigate to /cdrom and choose that directory.
[*]Press Start, now if you're lucky the game will start and you'll have sound from the CD and you can play to your heart's content. However if you're unlucky, like me, then you'll need to do a little bit more.
[*]Copy the CD's contents to a directory of your choosing, I used ~/Loom.
[*]Now in that directory, rip the audio tracks from the CD:
```
cdparanoia -B "2-"
```
This will create a file called 'track02.cdda.wav'.
[*]Now convert this to MP3:
```
sudo apt-get install lame
lame -t -q 9 -b 96 track02.cdda.wav track1.mp3

```
It is important that the file is called track1.mp3, so that the game can find it.
[*]Now in ScummVM use 'Add Game...' and choose the directory you copied the files into, i.e. ~/Loom, and press Start. You should now have sound. Enjoy.
[/LIST]

There are many other games you can run with ScummVM, see [www.scummvm.org](www.scummvm.org) for details.

I would recommend converting the audio track to FLAC instead.

sudo apt-get install flac

flac track02.cdda.wav

just rename the resulting file to Track1.flac

Should hopefully do the trick.

FLAC is lossless, so the sound is identical to the original CD, but 1/2 the size (mp3 is lossy, so it would give you maybe 1/12 the size, on the other hand you might as well rip to OGG, scumm handles them all fine...)
FLAC homepage for those interested
[http://flac.sourceforge.net/](http://flac.sourceforge.net/)

EDIT: Very nice how-to by the way. :)

---

