---
title: "MP3 Difficulty"
date: 2005-07-17
forum: Desktop Environments
---

### Post by Sephiriz on 2005-07-17
I recently acquired some MP3's, and they are being quite difficult.  Whenever I attempt to right click one of them in Nautilus, and then go to Properties, the folder freezes so that I need to Force Quit.  All other MP3's work fine except for this set of songs, yet I can still listen to them.

One other problem is that one of these songs had a tilde above the n (not quite sure how to reproduce it here).  I figured there might be a problem with that when I tried copying it over to my FAT32 HD that contains all my media, but even after replacing it with a simple "n", I still cannot copy it over without getting this error: Error "Invalid parameters" while copying "/home/max/Go... Manana.mp3 ".

Any help is appreciated, this is quite a nuisance and I have never stumbled across this before.  Might something be wrong with the encoding?

---

### Post by dickohead on 2005-07-18
[QUOTE=Sephiriz]I recently acquired some MP3's, and they are being quite difficult.  Whenever I attempt to right click one of them in Nautilus, and then go to Properties, the folder freezes so that I need to Force Quit.  All other MP3's work fine except for this set of songs, yet I can still listen to them.

One other problem is that one of these songs had a tilde above the n (not quite sure how to reproduce it here).  I figured there might be a problem with that when I tried copying it over to my FAT32 HD that contains all my media, but even after replacing it with a simple "n", I still cannot copy it over without getting this error: Error "Invalid parameters" while copying "/home/max/Go... Manana.mp3 ".

Any help is appreciated, this is quite a nuisance and I have never stumbled across this before.  Might something be wrong with the encoding?[/QUOTE]
 I experienced quite a few problems with Nautilus file browsing and MP3's aswell, the folder would just freeze and I'd have to force it to quit, eventually I found some corrupt files that I COULDN'T listen to, so I deleted them and was allowed access to the folder, and everything worked - I also experienced problems with the media player (jukebox something) when adding files to it - it would just freeze and I would have to force it to quit also.

Perhaps they are encoded in something that the mp3 libraries are unable to understand? you could try converting them on a windows machine to OGG and then to MP3... or leave them as OGG?

---

### Post by hydra on 2005-07-18
this might sound simple but I think maybe the problem is the name of the files ur copying its not the same to copy "/h"/home/max/Go... Manana.mp3 " than "home/max/Go... Mañana.mp3 ". So maybe its just a parameter error....maybee

---

### Post by Sephiriz on 2005-07-18
Well I changed the file name from the the "ñ" to "n", and then attempted to copy it over and it still didn't work.  Just for the sake of trying things, I changed the file name back to what it originally was, but nothing happened, same error.  

Ironically, this is the only file from that batch that I can succesfully look up the properties of without freezing up, although track info and such is displayed as "Unknown".

As to converting from mp3 to OGG back to mp3, aren't all these formats known for loss?  So that with every conversion, sound quality will reduce?  If I am correct in that regard, then I'd rather play the song from my home folder and live with not having it on my other HD.

Is there any error log that will somehow further detail what may have gone wrong?

Thanks for your efforts guys, I really appreciate it.

---

### Post by hydra on 2005-07-18
Well sound quality will reduce that's not absolutely sure but its quite certain...anyways why do u want to convert it to OGG and then back to .mp3??? 

[color=red]Error log: Error "Invalid parameters"[/color]

I think this one pretty much describes the prob...ur calling a file that is not on that dir or that is in that dir but its not its name..

any other errors shown up??

---

### Post by Sephiriz on 2005-07-18
Thats pretty much the error.  I tried copying the file via the terminal, but that didn't work either, I got the same exact error message.

I don't know how I could be screwing up the file name in Nautilus when I just try to click and drag from one folder to another.  It worked for all the other MP3's in the file, but this one file is being very difficult. 

I can play it, and I can move it around in my home directory, but I can't seem to move it to the FAT32 HD.  I'm wondering, is there some incapability on FAT32 to handle files with a UTF-8 charset?  Just wondering.

---

### Post by Sephiriz on 2005-07-18
Also, I don't know if this is relevant, but I sent one of the MP3's that I could move around but that would freeze on a right click to a Windows machine to get some info.  Here is what I got for this one song, and I assume all the other songs match:

Bitrate: 534kbps
Channels: 2 (stereo)
Audio Sample Rate: 44kHz

I don't know if this can help out any further, but better to have too much information as opposed to too little.

EDIT:  I just read the [this](http://ubuntuforums.org/showthread.php?p=260578) thread, and it leads me to believe that possibly RealPlayer 10 is causing the problem.  I'm not sure as of yet, and I have no access to my computer at the moment.  I'll update here later and see if uninstalling did the trick.

---

