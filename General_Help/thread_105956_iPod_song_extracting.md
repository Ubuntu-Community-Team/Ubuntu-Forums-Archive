---
title: "iPod song extracting"
date: 2005-12-19
forum: General Help
---

### Post by Cath0de on 2005-12-19
Hi, I want to extract the songs on my iPod and install them onto my hd. Is there any program that can do this? I've been tinkering with gtkpod and I can't find any function that would do that.

Sort of a noob question I guess.

---

### Post by briancurtin on 2005-12-19
this is entirely possible in gtkPod, however, i dont have my iPod here to walk through it. i did this on SuSE and have only been on ubuntu for a week and havent gotten around to this.

you want to read from your ipod, and then i want to say you use the Export Tracks from Database menu option and export the playlist or something. i know 100% that you can do in gtkPod what you are trying to do

---

### Post by Cath0de on 2005-12-19
sweet, yeah, I just figured it was something I didn't recognize

---

### Post by briancurtin on 2005-12-19
i just got my ipod out so i could help you get this going. heres what to do:

1. hook up your iPod and hit the Read button in the top left. let that work its magic and on the left panel you should see in bold YourName's iPod. click that so your music shows up in the panels on the right.

2. select a playlist from the left panel that you want to have on your hard drive. one of them will select all of your music, but i havent messed with that because im not ready to put all of my songs on just yet. i selected one track for this operation. 

3. go to File > Export Tracks from Database > Selected Playlist. that will dump everything in that playlist on your hard drive, but you have to tell it where in the next window and how you want it organized and all of that

hopefully that gets you in the right direction

---

### Post by Cath0de on 2005-12-19
okay, i did that

under how I wanted it saved, I put %o.mp3 (originalfilename.mp3), but I keep getting error messages like this:

Template ('%o.mp3') does not match file type '/media/ipod/iPod_Control/Music/F18/HZDQ.m4a'
Failed to write 'Weezer-Knock-Down Drag-Out'

---

### Post by aysiu on 2005-12-19
Can't you just copy the songs from your iPod? They're only files, after all.

---

### Post by briancurtin on 2005-12-19
you are specifying that you want NAME.MP3 ....but that weezer song is an *M4A*

all of mine were MP3s so it went smoothly, im not sure how you would go about that problem, but you could do any M4As individually (or in a group that you know are M4A) and specify them to be %o.M4A

thats just a guess, ive never had that problem before

---

### Post by briancurtin on 2005-12-19
[QUOTE=aysiu]Can't you just copy the songs from your iPod? They're only files, after all.[/QUOTE]
when my ipod was mounted, i looked in the folder it was mounted in and it doesnt contain the band names or anything like that, so it would require quite a bit of work to rename 6 GBs of music. it could be done that way though

---

### Post by shadow07 on 2005-12-19
[QUOTE=aysiu]Can't you just copy the songs from your iPod? They're only files, after all.[/QUOTE]

Um no.  Everything about the music file is stored in the iPod database on your iPod.  The song could be extracted from Nautilus, but that would be very time consuming, and you would have to re-add the MP3 or MP4 tags.

---

### Post by John Jason Jordan on 2005-12-19
[QUOTE=shadow07]Um no.  Everything about the music file is stored in the iPod database on your iPod.  The song could be extracted from Nautilus, but that would be very time consuming, and you would have to re-add the MP3 or MP4 tags.[/QUOTE]
That is correct. I Have never understood why Apple created such a bizarre system with the iTunes database. Plus it's about the most fragile thing ever created for a computer -- the slightest hiccup and the database gets corrupted. Then you're totally SOL -- reformat the iPod and start over. (Been there, got the t-shirt, too.)

Here's how I did it using gtkpod:

First, mount the iPod, launch gtkpod, and click on the Read button in the upper left corner of the gtkpod screen. That will display in gtkpod's windows what it finds in the iPod's iTunes database. 

I don't know if other users have gtkpod set up differently (hint to developers: some DOCUMENTATION would be nice!), but on my gtkpod I have three windows. The one on the bottom displays all your songs only if you select All from the window above. Otherwise it displays the tag info for just the item selected in the window above.

With all the songs listed in the lower window, select the ones you want to export. Right-click on the selection and choose Export Tracks. This will bring up a window where you can specify the folder you want them exported to. Then just click on OK and let gtkpod do its thing. I never attempt to rename a song in the process of exporting it. If I want to rename the file I do so after it is in the export folder.

I currentl have almost 20 Gb on the iPod, and all of them are saved in my "mp3_Exported" folder. These, in turn, are backed up with Dump to my external USB drive. Losing them was PITA and I ain't gonna go through that again.

---

