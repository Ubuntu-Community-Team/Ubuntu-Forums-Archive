---
title: "Music Directory Organizer"
date: 2005-02-19
forum: Desktop Environments
---

### Post by animalstyle on 2005-02-19
It doesnt seem like rhythmbox has an iTunes-like music directory organizer (automatically puts artist-album-song in 'recursive' directories based on song tags) does it?  Or is there any common easily installed program that does (like from the repository) ?  Wanna make life simple here  :roll: .

---

### Post by kassetra on 2005-02-19
well, [rhythmbox]("http://www.gnomefiles.org/app.php?soft_id=423") and [muine]("http://www.gnomefiles.org/app.php?soft_id=244") are both supposed to, but the only one I've seen work from the tag-based organization idea is [zinf]("http://www.gnomefiles.org/app.php?soft_id=433").  Zinf should be in your repository.  :)

---

### Post by animalstyle on 2005-02-19
hmm well, im pretty happy with rhythmbox, mainly I'm looking for a little side program kind of thing, maybe a more generalized program instead might be available?

---

### Post by kassetra on 2005-02-19
Try looking for [easytag]("http://www.gnomefiles.org/app.php?soft_id=415") ... the one in the repository seems to be the gtk1.x version, but if you add more repositories, you can probably find the gtk2 version, which is nicer.  :)
 
 Easytag won't organize them (I don't recall) into directories for you, but it can help you by cleaning up files names, tags, etc. so you could very easily dump a bunch of similarly named files (Artist-Album*mp3) into a directory...
 
 Or, you could install iTunes through codeweavers wine or cedega and have it organize all of your music files... 
 
 Hope that helps!

---

### Post by animalstyle on 2005-02-19
easytag...thats just what im looking for, i dont mind doing things manually so much, as long as it gets the job done.  Besides all I do is copy CD's over, that automatically get organized.  :---)

---

### Post by kassetra on 2005-02-19
great!  I'm glad I could help!  :)

---

### Post by luna6 on 2005-02-19
Try AMAROK......downloaded the brand spanking new 1.2 version and it is quite possibly the best linux app ever....downloads cover images from amazon, has a side panel view of all your music in a tree mode view, and other great things...like a suggested music part which i find amazingly accurate.....

---

### Post by kassetra on 2005-02-19
Well, amarok is a kde app, which means that a bunch of kde libraries would also have to be installed in order to make it work.  Also, it's not in the standard warty repositories, which means that upgrading to Hoary might take some extra work.
 
 As far as simplicity is concerned, installing amarok might not be the simplest route to take.

---

### Post by mtron on 2005-02-20
i use [madman](http://madman.sourceforge.net/) .  Very nice manager that uses xmms to play the files. If you have activated the extra resp. in your sources just  type "sudo apt-get install madman" (same for xmms)

Cheers

---

### Post by animalstyle on 2005-02-20
quote from madman homepage: 

" Smokes the competition.
More than likely you will have heard of Apple's iTunes. If you're a Windows user, you might have seen MoodLogic, MusicMatch or some others. If you already use Linux, you might have seen Rhythmbox, Yammi, JuK, Mp3Kult or Zinf. madman is pretty much in the same vein as all these. They all suck. All music managers suck. madman just sucks less. (Hm. Apologies to Michael R. Elkins :)) "

Okay I haven't tried the program yet but I have a VERY hard time believing that its better than iTunes, much less iTunes sucks....but hey, its all advertising right?  :wink:

---

### Post by machiner on 2005-02-20
I thought the job of organizing your music directory fell to the shoulders of your ripper. Ey?

Instance, I use sound juicer and it rips all nicey nicey right into the directories I instruct it to.

Conversly, when I run gtk-gnutella to download a song or two, I tell those to goto yet another directory within my music directory.

All is schweet. The only thing I have to do is correct all that malformed and bogus nonesense usually attached to any song I download. For that - easytag works very nicely.

All in a fine and easily navigable directory structure easily navigated by the likes of Madman or - whichever organizer you use.

Funny - I don't consider Madman (or the like) to actually be an organizer...just an easily viewable repository of my music -- pick some tunes - burn a disc.

Rock on.

---

### Post by kassetra on 2005-02-20
madman does seem very nice... I might have to try it some time... I'm not going to right now because I just switched from xmms to beep-media-player.
 
 Maybe I'll write the developers and ask for a bmp plugin... :)

---

### Post by ncappel1 on 2006-02-28
[QUOTE=machiner]I thought the job of organizing your music directory fell to the shoulders of your ripper. Ey?
[/QUOTE]

I should have joined this party a year ago! How's that for fashionably late?

I need a music organizer that will rename my files. The tags work great, but the problem is that I just moved them from my backup cds to my computer, and the files all have track names, but the file names are messed up. Anyone know if there is there a program that will read the tags and actually rename the files?

---

### Post by julipanno on 2006-07-19
> **ncappel1 said:**
> I should have joined this party a year ago! How's that for fashionably late?

I need a music organizer that will rename my files. The tags work great, but the problem is that I just moved them from my backup cds to my computer, and the files all have track names, but the file names are messed up. Anyone know if there is there a program that will read the tags and actually rename the files?

EasyTag will do that for you, no problem.. It's an excellent program for all tagging purposes, and in fact the only gtk app I use on my Kubuntu-laptop...

I've also just begun using Madman for browsing my music. The interface seems great, but it detects the encoding of the tags wrong (which are written by EasyTag and correctly read by other programs like XMMS and Nautilus). Does anyone know how I can force Madman to use a specific text encoding?


peace,
Stian

---

