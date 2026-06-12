---
title: "Amarok won't play some FLAC files"
date: 2006-07-02
forum: Desktop Environments
---

### Post by citizenkeith on 2006-07-02
I recently put all my FLAC files onto a FAT32-formatted drive, so I can create and save FLACs in both Ubuntu and Windows XP.

Today I noticed that Amarok was skipping some FLAC files. I couldn't figure out why, until I right clicked on the file and checked the properties. The files that won't play have "MP3" listed under File Type, even though they are FLAC files! I can play them in xmms without a problem, and the file information looks to be correct. See the two attached images for more information.

Is there an easy way for me to change the File Type? I'd hate to decode and re-encode all my problem files.

---

### Post by scxtt on 2006-07-02
what engine is amarok using? -- cause it looks like libflac has plugins for xmms, but if amarok is using gstreamer, and you don't have gstreamer-flac installed - well, that'd probably cause problems ...

---

### Post by citizenkeith on 2006-07-02
I'm using the Xine engine.

---

### Post by scxtt on 2006-07-02
my only idea right now would be to use (or install) the gstreamer engine and the gstreamer-flac package and use that w/ amarok, to see if it works ...

---

### Post by citizenkeith on 2006-07-02
[QUOTE=scxtt]my only idea right now would be to use (or install) the gstreamer engine and the gstreamer-flac package and use that w/ amarok, to see if it works ...[/QUOTE]

Thanks, I'll give it a shot. :)

Here's another clue. I just posted this in the Exact Audio Copy thread earlier today...

> 
I've been using EAC in wine to make FLAC files. I have the Compression tab setup to pass to FLAC.exe, which I copied over from my Windows partition.

When I look at the properties of each file (right-click > Propertied), it lists the File Type as MP3, even though it really is a FLAC file. In EAC, I have the compressor set to "User Defined," the extension set to .flac, and the following command line options:

```
T "artist=%a" -T "title=%t" -T "album=%g" -T "date=%y" -T "tracknumber=%n" -T "genre=%m" %s
```

The Bit Rate dropdown menu is still available, and it is set to 128 kBit/s. When I do this in Windows, it doesn't effect FLAC encoding.

For the most part, these are the files that Amarok can't play. It's either something in the EAC compression settings, or the fact that I use flac.exe in wine for encoding.

---

### Post by citizenkeith on 2006-07-03
I solved the problem. Instead of using flac.exe from my Windows partition, I downloaded Flac Tools for Windows and dumped flac.exe into the EAC directory. Then I went about setting up the compression properties according to this site:
[http://www.teqnilogik.com/tutorials/eac.htm#CompressionOptionsFLAC](http://www.teqnilogik.com/tutorials/eac.htm#CompressionOptionsFLAC)

Now it works fine. Go figure.

---

### Post by citizenkeith on 2006-08-29
It's happening again!!!!

The same thing as I reported in the first post... but this time, all the flac files were made with Grip. I can right click on a flac file, choose properties, and the "Type" is listed as MP3.

They are flac files... I used Grip with the proper settings and they have the correct file extension (.flac) and the proper encoding command lines... this makes NO SENSE!!

Is this a MIME type issue?

---

### Post by citizenkeith on 2006-08-29
After some additional searching, I came across this thread:

[http://www.ubuntuforums.org/showthread.php?t=222452&highlight=mime+mp3+flac](http://www.ubuntuforums.org/showthread.php?t=222452&highlight=mime+mp3+flac)

I ran EasyTAG on one of the offending files, and it fixed the problem. Now I'm going to run EasyTAG on the whole hard drive! :D

---

