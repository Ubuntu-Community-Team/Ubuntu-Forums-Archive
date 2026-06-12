---
title: "Problems ripping CD with japanese track names"
date: 2006-06-13
forum: Desktop Environments
---

### Post by shrimphead on 2006-06-13
I'm using dapper 6.06, Soundjuicer 2.14.3 and Grip 3.3.1 and I can't seem to rip a CD with japanese track titles.

In both cases the CD is picked up and the names display correctly in the application. When I choose to rip the track in Soundjuicer, it looks like it does it fine but the end result is an mp3 that is about 45-50Mb in size (for a 4 min track) and just consists of high pitched noise.

my sound gstreamer pipeline is:

```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=4 vbr-quality=2 ! xingmux ! id3v2mux
```

in Grip the mp3 is created and sounds fine, however there is no filename, it creates an mp3 called .mp3 (that is hidden due to the . prefix)

I get this in the status window when I try to rip a track

```
Grip started successfully
Ripping track 11 to /home/shrimphead/music/THE BACK HORN//.wav
Rip finished
1: Encoding to /home/shrimphead/music/THE BACK HORN//.mp3
Ripping is finished
Finished encoding on cpu 0
Deleting [/home/shrimphead/music/THE BACK HORN//.wav]

```

this happens despite the track names showing up fine in Grip and all the tag options being set to UTF-8.

Please help, this has been bugging me all day :(

---

### Post by shrimphead on 2006-06-13
Ripping occurs normally using Kaudiocreator in KDE however it is slow, idealy Grip would be awesome but if there's any way to reduce the paranoia settings in Kaudiocreator I'd be much obliged :D

thanks

EDIT: Kaudiocreator doesn't work properly :( It creates the filenames properly so they are viewable in konqueror but the ID3 tags are not in unicode and so don't appear in amarok properly

---

