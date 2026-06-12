---
title: "getting music to play in rythmbox"
date: 2005-09-26
forum: Desktop Environments
---

### Post by mitchelliscious on 2005-09-26
Hello i have installed all codecs and upgrades people have told me to install to try and play my music.  They are MP3's attached to a external hard drive.  When i try to play the music it comes up with 

Rhythmbox could not play 'file:///media/usbdisk/iTunes/Music/iTunes Music/2Pac/Resurrection/02 Ghost.m4a'.

There were no decoders found to handle the stream, you might need to install the corresponding plugins


thing is after that they say to install the corresponding plugins it doesn't show what pluggins to install.  I am running ubuntu and recently installed kbuntu which is awsome!!!  but thing is my music didnt work on both and installed both updates.  It says my music is .m4a but it is really a .mp3 is that something linux just does to play it?  also i know its not my speakers not working because when i run kbuntu the theme plays at the beginning when it loads, any help PLEASE!!!!

---

### Post by doclivingston on 2005-09-27
To play mp3s in Rhythmbox you need to have the package "gstreamer0.8-mad" installed, which is in the 'universe' repository. Playing m4a/mp4 tracks requires gstreamer0.8-faad, which is in 'multiverse' in Breezy - I'm not sure where it is in Hoary.

To check whether mp3 support is correctly installed, try running "gst-inspect-0.8 mad" from a terminal - it should print out information about the plugin, if it is installed.

---

### Post by kittycatsexycat on 2006-03-11
nice one mate you just sorted one of my problems too

---

### Post by dewey on 2006-03-13
I know this is an old post and I apologize, but running Dapper Drake with all the repo's uncommented out, I can't seem to locate the file with apt-get.
> 
Package gstreamer0.8-faad is not available, but is referred to by another package.
E: Package gstreamer0.8-faad has no installation candidate


Any help would be greatly appreciated.

Edit: Sorry, I found the thread using the search feature and didn't pay attention to the fact that it's in a 5.10 section.

---

