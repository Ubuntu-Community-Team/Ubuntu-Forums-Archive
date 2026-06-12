---
title: "how to add GPS data to exif fields? ??"
date: 2009-04-03
forum: General Help
---

### Post by quixote on 2009-04-03
I've found gpscorrelate & gebabbel.  So far, so good.  But I want to just type in a lat / long and have a program apply that to the exif data of a whole set of jpgs.  Those programs are expecting an input file from a GPS device or similar, which doesn't do me any good.

I have several hundred plant pictures.  Every 30 to 50 or so come from a different site.  I have an OLD OLD GPS device.  I'd take the reading at a given site, then take pictures.  What I'd like to do now is have an easy way to enter, for instance lat 35° 60' 36''   long 130° 45' 32''  into the appropriate exif fields of all the photos from a given site.  

Is there some way to do that with the above programs?  Should I be using something else?  I use gimp for processing.  Is there maybe an extension I haven't found yet that could do this?

Thanks for any help you can give me! :-)

---

### Post by quixote on 2009-04-08
Bump?  Nobody knows how to do this?  Say it ain't so!

---

### Post by Shwaa on 2009-04-17
Hiya,

I use Geotag to add tags to my photos, but I use the gpx files from my garmin.  Not sure if Geotag will do what you want.

You could add the tags via the command line using exiftool (sudo apt-get install libimage-exiftool-perl).

Something like:

```
exiftool -GPSLongitudeRef="E" -GPSLongitude="xx.xxxxxx" -GPSLatitudeRef="N" -GPSLatitude="xx.xxxxxx" /path/to/image
```
should do the trick.  You'll need to change the E and N to what is relevant to you.

This could be modified to add the tags to all the images in a directory.

NOTE: I'm not currently in a position to double check this at the moment, so I may be horribly wrong!

Hope that helps!

---

### Post by quixote on 2009-04-17
Thanks a million!  That gives me some idea how to start.  This looks like exactly what I need.

Update a day later:  I downloaded [geotag]("http://geotag.sourceforge.net/") --which has a GUI, which makes life easier for me -- and [exiftool]("http://www.sno.phy.queensu.ca/~phil/exiftool/") (which it depends on), and that's indeed *exactly* what I was looking for.  Very nice flexible programs.  You can enter lat - longs, you can correct them using google maps if you want, you can then copy the same data to whatever pics you select, or you can import GPS data files.  You can do anything.  Wonderful.

I'd mark this thread "solved" but that option seems to have disappeared.  "Thanks" have disappeared too.  Ah well, it's the thought that counts, right? :D

---

### Post by stani on 2009-06-08
The new version of Phatch will support this too:
[http://ubuntuforums.org/showthread.php?t=1178224](http://ubuntuforums.org/showthread.php?t=1178224)

---

### Post by quixote on 2009-06-08
looks nice, stani.  I'll have to try phatch on my next set of processing photos.

---

