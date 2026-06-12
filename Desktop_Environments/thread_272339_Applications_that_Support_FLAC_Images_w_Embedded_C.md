---
title: "Applications that Support FLAC Images w/ Embedded Cuesheets"
date: 2006-10-06
forum: Desktop Environments
---

### Post by VCSkier on 2006-10-06
When I used Windows, I had all of my cd's backed up in WavPack images w/ embedded cuesheets, and I did everything with Exact Audio Copy, foobar2000, and Burrrn.  Considering there is almost no WavPack support among linux native apps, I want to switch everything over to flac images with embedded cuesheets, but I need to find suitable software to do this.

I'm looking for some gnome friendly programs that support flac images with embedded cuesheets.  To create these images, I've been using abcde with the command ```
abcde -1 -o flac -a default,cue
```

It works very well, but I need other software that supports this to make everything work as I want.  I need a cd burning application that can burn from my images.  I need a means to split the images to tracks and encode them to mp3's, hopefully with proper naming and tagging (if not, I will have to use EasyTAG after the mp3's are created; not a big problem).  I will also want to apply album-based mp3gain to all of my mp3's.  Lastly, a player that supports the flac images w/ cueshets would be nice, but not essential, because I will be keeping my mp3 copies locally, and my flac images on an external hd for backup/archival.

I'm also open to suggestions for a different ripper if anyone thinks they know of a better one for my purposes.

I know thats alot to ask, but any suggestions or advice you can offer would be much appreciated.

---

### Post by danielph on 2006-10-23
I have been trying to encode and transcode using embedded cue sheets under Linux. It seems to be the most secure way of backing up CD's. I reckon the problems with playing and transcoding will become less as more people play with this format. For now there is an XMMS plugin that is based on the cdread plugin that is able to read FLAC files with embedded cue sheets. I have tried this on edgy and it seems to work OK. It is not readily available, but you can find more information [here]("http://www.mail-archive.com/flac@xiph.org/msg00258.html") 

Decoding is possible if you want to write a script or maybe there is one already out there.


I also replied to your [thread]("http://www.hydrogenaudio.org/forums/index.php?showtopic=48973") on hydrogenaudio with this.

---

### Post by danielph on 2006-10-23
[B][SIZE=5]Ripping with abcde FLAC w/ Embedded cuesheet[/SIZE]

To encode to a single flac with embedded cuesheet[/B]
```
 abcde -1 -a default,cue -o flac
```[B]To transcode from a single flac with embedded cuesheet
[/B]You can use your flac file to transcode to ogg, mp3 or wav etc whenever you need without needing to rip. It will create the files from the cd with id3 info.```
abcde -d [flacfilename]  -o [filetype][:filetypeoptions]
```See *man abcde* for more info

[B]To extract to a single wav file with original cue sheet for burning
[/B]```
flac -d <flac filename>
metaflac --export-cuesheet-to=FILE
```Hope this helps

---

### Post by VCSkier on 2007-12-19
Are there any cd authoring applications (burners) that support flac images and cue sheets?  I know k3b does, but I'm looking for something lighter and/or more gnome friendly.  Ideally, I should be able to give the application the cue sheet, or the flac with the cue sheet embeded, and it would reproduce the original cd, including all gaps.

---

