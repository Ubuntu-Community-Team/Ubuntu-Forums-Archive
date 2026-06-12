---
title: "Sound Juicer Can't Rip - &quot;File Not Found&quot;"
date: 2007-02-26
forum: Desktop Environments
---

### Post by eeefresh on 2007-02-26
I just tried ripping some CDs with the default settings in Sound Juicer, but I keep getting "Sound Juicer could not extract this CD.  Reason: File not found."

The weird thing is that it recognizes the CD and autoloads the tracks, and the CD will actually play from within Sound Juicer.  I tried several CDs and kept getting the same error.  Any ideas of how to fix this?

---

### Post by johnc4510 on 2007-02-26
Open Sound Juicer, click on Edit, click on Preferences
Make sure the proper drive is showing, and make sure a Music Folder is selected.
For this, you will need to first create a Music Folder in your /home directory. 
Then it should rip just fine. If not report problems back here.

---

### Post by eeefresh on 2007-02-26
Check, check and check.  The Lite-On CD-Rom drive is selected (my only disc drive), and the rips are directed to a music folder in my home directory.  I have CD Quality, lossy (ogg) selected for file type.  Still getting the same error.

---

### Post by johnc4510 on 2007-02-26
Boy, that's odd. Set up this way, it should put it right in the folder. Sorry, I don't think I can help.

---

### Post by eeefresh on 2007-02-26
I am using version 2.16.1 if that is any help.

---

### Post by ComplexNumber on 2007-02-26
i wonder if its a file that you haven't got that enables you to rip tracks. like an encoder or something.
do you have llame, gstreame0.8-lame, and liblame-dev installed?

---

### Post by eeefresh on 2007-02-26
I didn't install any of them, but I didn't (knowingly) make any changes to SoundJuicer.  How can I tell if I have those files?  I did a search in Synaptic, and none of those came up except the last one, which I didn't have installed.  Do I need lame for ogg files?

---

### Post by ComplexNumber on 2007-02-26
> **eeefresh said:**
> I didn't install any of them, but I didn't (knowingly) make any changes to SoundJuicer.  How can I tell if I have those files?  I did a search in Synaptic, and none of those came up except the last one, which I didn't have installed.  Do I need lame for ogg files?
firstly, you need to enable the multiverse and universe repositories. fire uop synaptic, go to settings in the menu, then repositories. tick all the boxes, then reload.
do a search on name only for "lame", "ogg", "gstreamer0.10", "cdparanoia", "libaudiofile-dev", "libid3tag". install all the relevant files. i don't know the exact ones which will rectify your problem, but it should be one of them.

---

### Post by eeefresh on 2007-02-26
I don't mean to sound ungrateful, but isn't that a little extreme?  Even when I select name only, those searches turn up a LOT of files...

---

### Post by aidanr on 2007-02-26
any errors when you run it in a terminal "sound-juicer", the last time i got this error, the music folder wasn't set in the prefs

---

### Post by eeefresh on 2007-02-26
Nope, no errors.  It started right up from terminal.

---

### Post by ComplexNumber on 2007-02-26
> **eeefresh said:**
> I don't mean to sound ungrateful, but isn't that a little extreme?  Even when I select name only, those searches turn up a LOT of files...
 its only "ogg" and "gstreamer0.10" that produces lots of files. 
install the following:
ffmpeg
vorbis-tools
libid3tag
gstreamer0.10-plugins-good
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-ugly


if i were in front of your PC, i could probably have it solved in a few minutes. but because i don't know what you have installed and what you haven't, its difficult to ascertain the culprit from where i'm standing. hope you appreciate.

---

### Post by eeefresh on 2007-02-27
I do appreciate your help, ComplexNumber.

I searched for all of those files in Synaptic, and it showed that they were already installed. I reinstalled them just in case something was corrupt.  No dice.  I still get the same "file not found" error.

---

### Post by ComplexNumber on 2007-02-27
> **eeefresh said:**
> I do appreciate your help, ComplexNumber.

I searched for all of those files in Synaptic, and it showed that they were already installed. I reinstalled them just in case something was corrupt.  No dice.  I still get the same "file not found" error.
oh dear. thats why i suggested installing them all (because i don't know which ones your missing). i usually just isntall all the audio/video stuff i can find. this includes all of the following: ffmpeg, mpegs, gstreamer, lame, fame, mad, ogg, vorbis, thora(video), swf, flac, mp3, sox, swh, timidity, faac, faad, mpg.

---

### Post by eeefresh on 2007-02-27
Maybe I am misunderstanding you.  When you say install them all, do you literally mean *all of them?*

For instance, when I do a search in Synaptic for "gstreamer," about 100 files come up.  This is with universe and multiverse installed.  I am hesitant to just start installing programs haphazardly  without knowing fully what they do.  Of course, I could read the descriptions, but as I said, 100 came up with that first search alone....

---

### Post by ComplexNumber on 2007-02-27
yup, all of them. they will come in handy for other purposes. honestly, it won't take you long at all. 5 minutes, at most.

>  For instance, when I do a search in Synaptic for "gstreamer," about 100 files come up.just "gstreamer0.10"



some packages have "dbg" at the end - you don't need to install them because they are debugging packages.

its not going to do any harm installing lots of those packages because they are only multimedia packages.


ok, looking through the above (eg ffmpeg, gstreamer0.10, mad, etc), do a search for them, and install the following for the time being:
ffmpeg - install all of them.
vorbis-tools - there's only 1
libid3tag - insrall all 2 of them
gstreamer0.10 - install the ones that i mentioned in post 12.


note that installing the above will also install several dependencies. install them too.

---

### Post by eeefresh on 2007-02-27
Well, I did exactly as you described, and yet I still get the same error.  

$&%!@#$@!!!!!

Pardon my outburst.  :-)

Thanks for your help, Complex, but I think I am going to have to give up on this one.  Can you recommend another ripping program, preferably with a GUI?

---

### Post by ComplexNumber on 2007-02-27
grrrrrrrr! damn it! i'm pretty certain its because there's a package that  isn't installed.
i doubt using another GUI will make any difference.

---

### Post by eeefresh on 2007-02-28
I downloaded Grip and experimented with it.  Took me a while to get it set up right, but it seems to work fine.  Go figure!

---

### Post by reidi on 2007-03-03
I got this vague error message because I was attempting to write to my external USB mass storage device, which is formatted as NTFS.  NTFS is still normally read-only for most Linux users, except for the bravest using non-production machines.

Ubuntu 6.10 'Edgy'
"Enough multimedia libraries, codecs and software loaded to play Real media, BBC, MSNBC.com, CNN.com video, etc."

---

### Post by clarkej on 2007-05-06
Maybe your ownership or permission to write the file is wrong? 

In my case chown solved the problem - the 'file not found' error was because root owned the destination directory.

---

### Post by rodericj on 2007-07-23
I have just had this error after using SoundJuicer for months without a problem. The machine had crashed, for the first time ever, and after being re-started this error appeared. It was easily cured by going into Edit - Preferences and resetting the directory where the ripped tracks were stored.

The reason the machine crashed might have been due to todays updates for CompizFusion. After the updates I tried compiz - again and it did not work properly. I returned to Beryl - which has always been fine and stable for me.

---

### Post by paulphillips on 2007-07-29
I also got this error.

In preferences, my home directory was set as the default location (which I thought should have been ok).  I changed this to another directory that I create especially for ripping and error went away.

---

