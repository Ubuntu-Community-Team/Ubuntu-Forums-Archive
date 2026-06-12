---
title: "Banshee MP3's"
date: 2006-06-19
forum: Desktop Environments
---

### Post by Max Roswell on 2006-06-19
Hey, there...

I'm not sure if this is the right forum, but here goes.  I got fed up with Rhythmbox and switched to Banshee, and like it a lot, except I just discovered that my MP3 player chokes on MP3's ripped/encoded by Banshee.  It can see the ones I'd done with Rhythmbox just fine, but doesn't see the Banshee ones.

As near as I can tell, the differences in the files seem to be that Rhythmbox is VBR and Banshee is CBR; Rhythmbox is 128 bitrate, Banshee is 160; and Banshee seems to leave out some ID3 tags.

Any guesses which of those might be confusing my (very basic, very crappy) MP3 player?

---

### Post by Max Roswell on 2006-06-19
Following up my own post.

The problem seems to be that my MP3 player won't play anything without ID3v1 tags.  Banshee doesn't seem to put them in there.  What do I change in Banshee to make that happen?

---

### Post by gamma on 2006-06-19
I think there is some kind of bug of with rhythmbox's tag support. If you edit an id3 tag it won't save the tag either, it just stores it in Banshee's database. Banshee seems to look up all the data using Musicbrainz or something and fills the album data just for Banshee. If anyone knows a fix let me know, but of course I just realized it didn't write tags recently, so I have lots of mp3s without tags :/.

---

### Post by aysiu on 2006-06-19
You can bulk copy ID3 v.2 tags to v.1 tags with the *kid3* program. ```
sudo aptitude update
sudo aptitude install kid3
kid3
``` It's in the Universe repositories, but if you have Banshee, you probably have those enabled already.

---

### Post by Max Roswell on 2006-06-20
Well, I found that I can use Audio Tag Tool to do what I want, but it's kinda sad that I have to add a step to the whole process.

What I need is a ripper that will create the ID3v1 tags when it rips.  Banshee doesn't, Sound Juicer doesn't.  Does Grip?  I looked at it and it looked quite intimidating.

This is an unnecessary pain in the arse.  Isn't this a pretty basic thing to ask of a ripper?

---

### Post by aysiu on 2006-06-20
You might want to look at Goobox or KAudiocreator. I think one of those does ID3v1 tags.

TagTool I believes copies ID3v2 to ID3v1 only one song at a time. With KID3, you can bulk copy tags.

---

### Post by Max Roswell on 2006-06-21
Just to close the loop, I took the time to figure out Grip and have decided to just use that for my ripping and encoding needs.  It does everything in one step, so I won't have to go back and edit any tags later.  I still like Banshee as a player, but not as a ripper.

---

### Post by aysiu on 2006-06-21
As far as I know, Banshee doesn't do its own ripping but secretly calls on an external program to rip for you. Is there a way to associate Grip with Banshee?

---

