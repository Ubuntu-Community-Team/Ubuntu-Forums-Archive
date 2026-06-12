---
title: "Import from Adobe Photoshop Album"
date: 2005-05-19
forum: Desktop Environments
---

### Post by szdavid on 2005-05-19
Hello,

With windows, i am using Adobe Photoshop Albums but there are about 3,000 pictures and I'd like not to reorder every one in the good category ; do you know a linux software in which we can import some Adobe Photoshop albums/backup ?

Thx

---

### Post by cometdog on 2007-07-30
Ancient post, but I'm still not aware of a good solution and I'm curious to see if anyone else is.

I'm in exactly the same situation, and the only option I have found yet is iMatch (Windows software).
[http://www.photools.com/](http://www.photools.com/)
It's not free, but it has a 30 day trial version that is completely unrestricted.  Someone wrote a script (scripting language is Sax Basic, IIRC, so it's pretty easy to follow) that will read your photoshop album database information and import it into iMatch.  From there it should be possible to write the information directly into the image files if you so desire, but I haven't really messed with that yet.  Also seems likely that the script could be altered to do this directly, but again I haven't really looked into this.

If I get a little inspiration to mess with this more some day soon, I'll let you know if I'm able to work it out.

Has anyone else tried this?  My goal is to get the tags I had in Photoshop Album written into the meta-data fields of the image files, so that the info travels with them and I can access it anywhere.  I know serious photographers often consider this a no-no because I am risking corrupting the images.  But hey, that's what backups are for.  And I've had it with the proprietary database.  Writing directly to the image files seems the only way to guarantee simple portability.

Any recommendations for which kind of meta-data fields to use (I think there's something called IPTC, maybe something else with an X in it somewhere, etc.) so that photo organizing tools in Linux can make sensible use of the information?

---

### Post by afsahabi on 2007-12-19
I moved to Linux about a month ago and this issue remains one of the obstacles.
Did you follow up with iMatch script? Could you finally import your Adobe Album data?

Let me know if there is any progress.

Many thanks.

---

### Post by KOld Iron on 2007-12-26
Hi, the key is to get your Windows application to write the tag information as IPTC information directly into the picture (as already said in some previous posts). This applies for JPEGs only. I had used Photoshop Elements and supposedly that is possible there. For some reason it only worked for some pictures. I didn't follow up the reasons why it did not work, but re-tagged most of my photos again (a few hours work, but manageable).
Anyways the application I use with Ubuntu is digiKam. Although it is a KDE application, I run it under GNOME, since it serves my needs much better than for example f-spot. It has a similar feature set as Photoshop Elements, but better filters! Anyways, digiKam can also read the IPTC information and you can re-use the keywords as tags in digiKam.
Hope this of some help.

---

### Post by afsahabi on 2007-12-31
Thanks for your reply! It put me on the right track.
I had started writing SQL scripts to take my tags from Adobe Album to F-Spot, but your suggestion is a lot better: Files will carry tags (keywords) and will become more portable.

This is what I did: 

[LIST]
[*]New Photoshop element 6 has an option to write keyword tags to the files. I downloaded it and used the 30 day trial to convert my old Album v2 tags to 'keyword tags' and write them to the files.
[*]Moved to digiKam: Way better application (compared to F-Spot) with excellent features: Thanks again for this hint!
[*]Used the root of my picture library as digiKam album library folder to avoid digiKam making extra copies (no option to import without copy)
[*]Bingo! I'm in business :) - I could not afford re-tagging close to 9000 photos.
[/LIST]

One thing I miss in didKam is: setup a slide show as screed saver.

Cheers!

---

### Post by KOld Iron on 2008-01-01
Hi afsahabi,

glad I could help. I just checked digiKam and there is a feature to set up a slide show (never used my self though), but it creates a separate MPEG file. I guess you were looking for something like providing a folder and then the screensaver is just cycling through the pictures. And although there is a GLSlideshow in the Ubuntu Screensaver Preferences, it is not clear to me, which directory it is referencing (it is not configurable, at least I couldn't find it).

The one thing I am missing in digiKam is working with layers. Although I only use this from time to time, it was a nice feature in Photoshop Elements for masking certain parts of a picture for selective editing. Of course, with Gimp this should be easily possible, but like many people I have kind of avoided the learning curve there until now. Maybe Krita (another KDE program) is able to do that. But having switched to Ubuntu just recently I am still evaluating what works best for my purpose. digiKam certainly covers most of what I need already, so I certainly will keep using with it.

Apart from that, I just wish you a very happy New Year 2008.

---

