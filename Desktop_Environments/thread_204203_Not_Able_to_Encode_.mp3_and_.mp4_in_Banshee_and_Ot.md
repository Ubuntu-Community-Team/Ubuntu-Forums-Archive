---
title: "Not Able to Encode .mp3 and .mp4 in Banshee and Others"
date: 2006-06-26
forum: Desktop Environments
---

### Post by General_Tso on 2006-06-26
Hello, folks.

In the preferences dialogue of Banshee, there are only encoding options for Ogg, Flac, and Wave/PCM.  The same is true for Sound Juicer.  I have lame installed as well as gstreamer-plugins.  How do I enable encoding option for .mp3 and .mp4?  I'm drawing an absolute blank.

Thanks!

---

### Post by murph2481 on 2006-06-26
This is how I did it:

Download Sound Juicer

Make sure multiverse is available - Change all universe words to multiverse in sources.list

go to a terminal and type: sudo apt-get install gstreamer0.10-plugins-ugly-multiverse

edit Sound Jucier settings
Add a profile
For Gstreamerpipline have:
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc bitrate=128

Save and exit Sound Juicer

Then restart Sound Juicer and select options and choose MP3

---

### Post by General_Tso on 2006-06-26
Thanks!  That did it!

---

### Post by miggl on 2006-12-06
Thanks for a very excellent tip!!!:KS

---

### Post by radiobuzzer on 2006-12-12
Sorry, this didn't work and resulted to a disaster. I had been given two important CDs I had to rip within two hours. 
I am on a AMD 64x2, having the 'ugly' package mentioned above installed.

I used the tutorial above, so the CD appeared being ripped. After some time, I realised that the .mp3s created were 700MB each, and that they couldn't be played. Even the audacity is unable to open them. Of course I gave back the CDs and now I have to try to find what has hapenned to these ruined Mp3 files, cause there are people waiting for me to make copies. 

It's an awful situation. I wish I wouldn't have trusted linux for this job.

---

### Post by black_magician on 2007-02-10
thanks so much man,  that works great!

---

