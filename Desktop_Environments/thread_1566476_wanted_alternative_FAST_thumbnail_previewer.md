---
title: "wanted: alternative FAST thumbnail previewer"
date: 2010-09-02
forum: Desktop Environments
---

### Post by betlog on 2010-09-02
Can anyone suggest some way to substitute the default KDE thumbnail previewer with a more speed efficient one?
I assume the default kubuntu one is dolphin based, I do like dolphin, but for uploading files from firefox etc I need something that can preview the thumbnails much faster. I see various issues with thumbnails all through the search results, so i am posting to highlight my particular issue, and what I see as a possible improvement in the thumbnailing system in general.

NOTE: I am pretty sure this is the crux of this issue: **In dolphin I sort all '/pictures' subfolders 'by date - descending'**..not 'by name'
As i understand it, the speed issue is related to several points:
-images have to be hashed so as to know which thumb to get <- kind of unavoidable
-images, and therefore thumbs are retrieved by alphanumeric sorting <- COULD BE SPEED-IMPROVED

The problem:
Attempting to preview a thumbed-folder which is large.. is SLOOOW (10000 files in some cases, but even 1000 is noticeable, and a short wait)  despite :
1) having  set thumbnail cache to 5Gb, and 
2) making sure all my desired image folders are properly thumbnailed (I let them load and then scroll through to check), and 
3) checking that they do indeed fit in the cache size so they arent lost betweeen sessions
But when I try to view a folder with a large number of images, the preview window either locks up for a while (several whole minutes), or noticeably slows the entire system **while the thumbnails jump around into their correct sort sequence...for several whole minutes**.. selecting a file while this shuffling is happening is possible, but mostly achieved by pure chance.

What makes this particualrly annoyng, and noticeable, is that generally the image I want is almost always going to be at the top of a 'sort by date' list, and therefore should appear on the very first page of previews/thumbs, yet despite this I have to wait for the images to shuffle around as they are retreived 'by name', this means that potentially a significant portion of the total number of thumbs need to be loaded before even the first page of results can be displayed.
Even if I keep Dolphin open and the folder of thumbs fully loaded, any other preview window I open (image upload to the forum for example) will have to repeat the loading of thumbs.

I notice that gthumb seems to deal with this fairly well, but gwenview just crashes, so much that I am tempted to totally remove it

I have made feature requests... but I doubt any developers will really comprehend  unless they experience the issue first-hand...and I don't think that many software developers have very high image perusal requirements. :] So please put your thoughts here and on the feature requests below.

feature requests:
thumbnail retreival should be sequenced by folder sort order 
[http://brainstorm.ubuntu.com/idea/25678/](http://brainstorm.ubuntu.com/idea/25678/)
user-definable and/or self adapting thumbnail cache sizes
[http://brainstorm.ubuntu.com/idea/25679/](http://brainstorm.ubuntu.com/idea/25679/)

related posts:
[http://ubuntuforums.org/showthread.php?t=1348050]("http://ubuntuforums.org/showthread.php?t=1348050&highlight=thumbnail")
[http://ubuntuforums.org/showthread.php?t=1536377]("http://ubuntuforums.org/showthread.php?t=1536377&highlight=thumbnail")
[http://ubuntuforums.org/showthread.php?t=1483356]("http://ubuntuforums.org/showthread.php?t=1483356&highlight=thumbnail")
also related:
[http://ubuntuforums.org/showthread.php?t=1331127](http://ubuntuforums.org/showthread.php?t=1331127)

---

### Post by betlog on 2010-09-05
Bump because this issue seriously sucks.

---

### Post by weblordpepe on 2010-09-05
> **betlog said:**
> Bump because this issue seriously sucks.

Hey dude I know that there is a way to specify which program runs when gnome wants to thumbnail a picture (i found it somewhere using gconf-editor) but I have no idea for KDE.

Its as simple as a command line. dunno where to find it tho. Im sure if you found an alternative program it would be alright.

---

### Post by betlog on 2010-09-06
Hmm. I can see options in gconf-editor for what appears to be selecting the application that creates thumbs for xml and html, but thats a bit different to wanting to replace the entire thumbnail renderer.
I am pretty sure I have just found the one thing I really don't like about dolphin. So either I remove & replace dolphin, which would suck, or I try to get the dolphin devs to fix it.
 To be honest I am finding it hard to believe that nobody has noticed this before. I mean seriously, every time I browse a large folder I can literally see the lifespan of my drive diminishing ever so slightly as the drive reads/s graph in ksysguard jumps up, and stays up for several minutes. It's ridiculous.

---

