---
title: "How would I convert my music files?"
date: 2006-06-30
forum: Desktop Environments
---

### Post by Xzallion on 2006-06-30
I have just spent about 30 minutes searching the forums trying to figure out how to convert .mp3 and .wma files to either .ogg or more preferably to flac.

I tried out the program called soundconverter, but It doesn't seem to do anything.  Any suggestions?

---

### Post by FISHERMAN on 2006-06-30
[QUOTE=Xzallion]I have just spent about 30 minutes searching the forums trying to figure out how to convert .mp3 and .wma files to either .ogg or more preferably to flac.

I tried out the program called soundconverter, but It doesn't seem to do anything.  Any suggestions?[/QUOTE]
Sound converter still works with gstreamer 0.8(Dapper has gstreamer 0.10).
If you install all the gstreamer 0.8 packages soundconverter will work fine.

---

### Post by AZzKikR on 2006-06-30
Audacity supports converting mp3's to ogg, but I do not know if it supports batch converting. Something recalls me that it does, but you could take a look at it:

[Audacity on Sourceforge.net]("http://audacity.sourceforge.net/")

---

### Post by Xzallion on 2006-06-30
Cool I will give that a try, but out of curiosity, why don't the new gstreamer 0.10 packages work for soundconverter?

---

### Post by ajgreeny on 2006-06-30
Have a look at *sox* in the terminal - type *man sox* for lots more detail. I don't know much about *soundconverter* or the kde version *soundkonverter,* but I suspect they may use *sox* to actually do the job beneath the gui.  I have used sox to convert ogg to mp3 and it's quick and easy.  I am not sure if you can do a batch conversion, however, as I think all the input files are joined into one large file with all the originals one after the other.

---

### Post by frodon on 2006-06-30
I'm more than happy with audioconvert : [http://ubuntuforums.org/showthread.php?t=82806](http://ubuntuforums.org/showthread.php?t=82806)

---

### Post by Raezel on 2006-06-30
Just wondering, how big is the quality loss when converting from mp3 to ogg?

---

### Post by FISHERMAN on 2006-06-30
[QUOTE=Xzallion]Cool I will give that a try, but out of curiosity, why don't the new gstreamer 0.10 packages work for soundconverter?[/QUOTE]
Because the people behind sound converter haven't included support for 0.10 yet.(the next version of sound converter is planned to work with 0.10)

---

### Post by FISHERMAN on 2006-06-30
[QUOTE=Raezel]Just wondering, how big is the quality loss when converting from mp3 to ogg?[/QUOTE]
Depends on the selected bitrate.

If you choose ~500 kbs you'll not notice a difference.
But if you choose ~64 kbs you'll probably have a big quality loss.

When I converted my MP3 collection to OGG I didn't hear a difference on 192 kbs.

---

### Post by Xzallion on 2006-06-30
I just installed the audioconvert script, as suggested in Frodon's post.  It works, but it has to be done manually for every file, and I need a ton of files converted. (Approximately 1300 in .mp3 and .wma formats).  Is there a way to make it do a batch conversion?

And I took a look at the gstreamer 0.8 packages, would I need to install all of them?  Cause there is like fifty of them!  I looked through it and found the vorbis, flac, and lame packages for gstreamer 0.8, what others would I need besides these to get soundconverter going?

And thanks for all the help guys, I appreciate it.

Edit:  audioconvert can only make .wav and .flac for me, it won't make .ogg.  It just says it has finished converting it and stops, but there is no file made from it.  And I didn't realize that the lossless flac file size would be so huge!  I converted a 4.4MB  song to flac, and it was suddenly 24.4MB!  Is this correct, or is something wrong with it?

---

### Post by newman on 2006-06-30
What's the main advantage of having ogg vs. mp3?  I'm asking because all my cd 's were ripped to mp3 when I was using windows, and I ripped most of them at 192 or 256k.  Now I've ripped a few cd's in SoundJuicer with the default ogg setting...

---

### Post by Xzallion on 2006-06-30
I'm not sure if there is a real advantage, some say that ogg has a better compression then mp3, so the file size is smaller.  I just want my music in a open format, because apparently here in the U.S. some formats are not allowed to have their codecs on linux, im not sure if .mp3 is one of them.  I would just rest easier knowing I could always listen to my music in ubuntu, no matter what kind of crazy laws get passed.

---

### Post by frodon on 2006-06-30
[QUOTE=Xzallion]I just installed the audioconvert script, as suggested in Frodon's post.  It works, but it has to be done manually for every file, and I need a ton of files converted. (Approximately 1300 in .mp3 and .wma formats).  Is there a way to make it do a batch conversion?

And I took a look at the gstreamer 0.8 packages, would I need to install all of them?  Cause there is like fifty of them!  I looked through it and found the vorbis, flac, and lame packages for gstreamer 0.8, what others would I need besides these to get soundconverter going?

And thanks for all the help guys, I appreciate it.

Edit:  audioconvert can only make .wav and .flac for me, it won't make .ogg.  It just says it has finished converting it and stops, but there is no file made from it.  And I didn't realize that the lossless flac file size would be so huge!  I converted a 4.4MB  song to flac, and it was suddenly 24.4MB!  Is this correct, or is something wrong with it?[/QUOTE]To use correctly audio convert you need some libraries, this guide will help you (even if it is for breezy) : [http://doc.gwos.org/index.php/Audio-convert](http://doc.gwos.org/index.php/Audio-convert)
To convert more than one file quickly, add the script to the nautilus scripts directory then just select all the files to convert in nautilus and right click the selection to apply audioconvert on the selection.

---

### Post by yaztromo on 2006-06-30
Converting from one lossy source to another (mp3 to ogg) will incur much more quality loss than if you converted from the orginal CD.

I suggest if you have the original CD's, rip them to wav and then convert to OGG.

---

### Post by Xzallion on 2006-06-30
I just used that how-to frodon, and for some reason it didn't work at step 2.  It won't download the first two wget things.  gives me a "404 not found" error in the terminal.  still no support for ogg on my machine :(

I realize ogg is lossy, but I either have lost the cd's, or its music that didn't come from cd's (Most of it, about 1300 of the files) is from [OverClocked Remix]("http://www.ocremix.org/").  I won't notice a huge loss in sound quality, so unless the conversion will turn a good mp3 into a horrible thing that sounds like you ripped it off analog fm radio, I will be happy with it.

---

### Post by frodon on 2006-06-30
The links should be broken, anyway you could find the .deb elsewhere, they enable .mpc and mac support.
For ogg support you only need the vorbis-tools package so if you installed it yet it should work, sorry to not provide you more help.

---

### Post by Xzallion on 2006-06-30
Thats allright, at least you tried frodon, and I appreciate it.  Guess something just isn't clicking on my system.  Im going to muck around with it some and see if by some miracle I can just somehow get it working.  Or maybe someone else will stop by and post a fix.

I figured it out.  It was something obvious I missed.  I was testing this on a file I had moved to my desktop, and while it would let me use the script, it wasn't actually doing anything.  By opening up the file browser (nautilus) and browsing to my desktop, and running the script inside it it works.  Sorry about wasting so much of your time on my mistake.

I uninstalled and re-installed all the gstreamer 0.8 packages, using the handy all plugins thing in synaptic.  After doing this, soundconverter works to.  So I guess I have both working now.  :D
Thanks Everyone for you help!

---

