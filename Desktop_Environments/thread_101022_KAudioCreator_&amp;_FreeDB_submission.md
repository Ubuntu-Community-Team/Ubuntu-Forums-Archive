---
title: "KAudioCreator &amp; FreeDB submission"
date: 2005-12-08
forum: Desktop Environments
---

### Post by gingermark on 2005-12-08
Can anyone categorically confirm or deny that KAudioCreator can submit information to FreeDB? Under the CDDB section in the program's settings there is a "Submit" tab where one can set the program up send data to FreeDB (via HTTP or email) but I can't for the life of me find a "Send" button, and there's bugger all documentation.

I know that KAudioCreator puts the info in the /home/username/.cddb folder, although the files created by it seem to be missing disc id info. Is there a program available that can determine a CD's disc id? It might seem an odd work-around, but it occurred to me that one could then manually email the data to FreeDB. Whilst not ideal, it would be quicker than using another program and having to type everything again just to submit it (assuming one wants to use KAudioCreator to rip & encode their CDs, which I do).

KAudioCreator is the best ripper & encoder program (with a GUI) that I've found for Linux, although when you compare what's available to the mighty EAC that's not saying much. Pity EAC wasn't release under the GPL....

Anyways, any answers or ideas would be greatly appreciated.

Many thanks,
gingermark.

---

### Post by ftavares on 2006-05-23
KsCD's freedb submission is working really well now. You should give it a try.

---

### Post by flamir on 2007-07-09
I bump this one now ...

I cant find any submit button either ... where is it ? or what can i use to submit stuff ?

---

### Post by Brindled on 2007-07-09
> **flamir said:**
> I bump this one now ...

I cant find any submit button either ... where is it ? or what can i use to submit stuff ?

I used this for the first time today, and after setting up which codec (mp3) I wanted to rip with, it automatically looked up the CD upon putting the music disc in the drive. 

There was no need to push any submit button, however, there is a submit tab in the CDDB section of KAudio Creator's configuration .

hope this helps.

Edit: Upon further inspection, hahaha, I've located the button (see pic).
[IMG]http://img384.imageshack.us/img384/1381/kacssgb1.jpg[/IMG]

---

### Post by flamir on 2007-07-16
well thats not the problem , i have several cds that are not in freedb yet . thats why i want to submit my info to freedb . found that stuff in the configs too but thats it :/.

---

### Post by nlaw on 2007-09-26
I have the same problem with KAudioCreator, however there is a workaround....

You already know that when you enter track info using KAudioCreator it places the disc ID and track / artist info in .cddb.... well 'Grip', another Ripper accesses this directory and Grip does have a Submit button for sending the track info to freedb.

So the procedure I use is ...
1. Put Disc in Drive
2. Run KAudioCreator
3. Edit Track Info, Artist Info, Title, years etc ..
4. Rip Disc using KaudioCreator
5. Exit Kaudiocreator.
6. Leave the CD in the drive.
7. Run Grip, The track info will be filled in because it accessed .cddb
8. Press the submit button (near botton right hand corner of the Tracks tab)
9. Check freedb.org, search for title and the CD info should now be listed.

There is another, more seamless way to rip a CD if you use Amarok and Konquror. (assuming your using KDE)

1. Simply open Konqueror, in the URL field type audioCD:\
2. The CD will be listed with correct track names etc as konqueror accessed freedb. There will be an Ogg folder and a mp3 folder, Go into which ever format you want to rip then select all the tracks (CNTL-A) and drag them onto the 'Collection tab in amarok. (Click on the Collection tab first to display your current collection) They will be ripped on the fly and added to the Amarok collection automatically.
3. As far as I'm aware Amarok cannot submit track info to freedb (correct me if I'm wrong) but it does access freedb for track info.


Regards
Nick

---

### Post by alainhenry on 2007-09-29
Related problem: my Grip "submit" button does not seem to do anything.  I have the default configuration settings, except for the e-mail, where I entered my address.  Any idea how I could "submit" to freedb ?
Thanks

---

### Post by alainhenry on 2007-10-08
Indeed, KsCD does the trick.  I could submit information to freedb using it.

---

