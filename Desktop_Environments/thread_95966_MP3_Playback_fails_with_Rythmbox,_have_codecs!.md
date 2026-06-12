---
title: "MP3 Playback fails with Rythmbox, have codecs!?"
date: 2005-11-27
forum: Desktop Environments
---

### Post by | MM | on 2005-11-27
Hi,

I have searched the forums regarding this issue and indeed many people cannot et media playback because they lack specific codecs.  However, as far as im aware i have the codecs and yet it still will not play mp3's.

I have the AMD64 version of Ubuntu Breezy.

Hopefully that screenshot illustrates the fact that i have installed many of the codecs (including the mad codedc for mpeg formats) from synaptic and i have updated the registry.xml via gst-register-0.8.

Note that none of the .mp3 are playing, resulting in the "could not open resource for writing" dialouge in the file properties within Rythmbox.

Also worth mentioning perhaps is that the music files reside on a WindowsXP NTFS partition.

I had Rythmbox working on the last incarnation of Ubuntu, that being Hoary.  It too was an AMD64 installation.  And i did not have this trouble, i simply followed the Starter Guide.


Any guidance would be much appreciated.  As i am at a loss.

---

### Post by Brent Dax on 2005-11-27
[QUOTE=| MM |]Note that none of the .mp3 are playing, resulting in the "could not open resource for writing" dialouge in the file properties within Rythmbox.

Also worth mentioning perhaps is that the music files reside on a WindowsXP NTFS partition.[/QUOTE]
Time to start eliminating factors.

1. Copy an MP3 from the NTFS partition to the Linux partition.  Does it still refuse to play?
2. Try playing a file in a different format, such as Ogg Vorbis.  (If necessary, you can grab an audio CD and rip a track from it.)  Does it work?
3. What about an Ogg file on the NTFS partition?

(Oh, and what theme are you using?  It looks pretty nice.)

---

### Post by sevenrechlin on 2005-11-27
I could never get rythmbox to work for me as well, so I installed amarok and it works great.

"sudo apt-get xmms*"
"sudo apt-get amarok*"

---

### Post by aysiu on 2005-11-27
[QUOTE=| MM |]
Note that none of the .mp3 are playing, resulting in the "could not open resource for writing" dialouge in the file properties within Rythmbox.[/QUOTE] NTFS is read-only, but that shouldn't affect you *playing* the MP3s.

I'd take Brent Dax's advice. If the copied MP3 plays, it's a permissions issue. If it doesn't, it's a codec issue.

---

### Post by cdhotfire on 2005-11-28
Ive had this problem before, you can either go to System -> Preferences -> Multimedia Systems Selector, and choose ESD output, OSS input. It should let you play then. Or you can do this[ http://www.ubuntuforums.org/showthread.php?t=79959&highlight=esd]("http://www.ubuntuforums.org/showthread.php?t=79959&highlight=esd") and then change both input and output to ALSA.;)

---

