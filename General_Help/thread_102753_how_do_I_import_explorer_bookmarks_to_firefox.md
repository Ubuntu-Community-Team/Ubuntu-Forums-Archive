---
title: "how do I import explorer bookmarks to firefox?"
date: 2005-12-12
forum: General Help
---

### Post by franohern on 2005-12-12
When I have installed firefox on my windows machines in the past, it has offered to import my explorer favorites. Is there a way for me to import my explorer favorites from a windows partition on the computer I use to run ubuntu? I've tried using the import feature under manage bookmarks, but back when it was working I could only import one page at a time, and lately when I tried even that, nothing happed. It would be great if I could get my explorer bookmarks into firefox on ubuntu, as I have been collecting them for a number of years and have managed to tranfer them through numerous re-installs of windows.

Thanks,
Fran

---

### Post by wylfing on 2005-12-12
There isn't going to be an equivalent feature. You could try copying the bookmarks.html file from Firefox on Windows over to your ~/.mozilla/firefox directory and that should work fine.

If you want to keep your bookmarks synced between Windows and Ubuntu, you should investigate one of the bookmark synchronizer extensions. Some people claim success by symlinking their Linux bookmarks to their Windows partition, but I always had failure doing that, and I no longer have a Windows partition to experiment on these days.

---

### Post by blair on 2005-12-12
You didn't mention whether you are trying to move the bookmarks from one partition to the next or from one computer to the next. One easy method is to simply export from IE to a file. Then email it away to yourself. Now the file is off of PC 1/partition 1. Then fire up your linux distro, retrieve the email and save the attachment to your desktop or home folder. Open up Firefox, Select Bookmarks >  File > Import > From File > browse to your file. 

If for some reason the IE to Linux Firefox export/import doesn't works, try the IE > PC Firefox > Linux Firefox path, i.e. do 2 steps. Firefox PC can definitely import from IE and Firefox Linux can definitely import from Firefox PC. 

I'm sure others may have more elegant solutions, but this should work.

---

### Post by djlilyazi on 2006-01-11
i need my bookmarks....does anyone know how to do this ?

---

### Post by aysiu on 2006-01-11
Can we assume this won't work for you, for whatever reason?

1. Boot into Windows.
2. Load up Firefox. Manage Bookmarks. Import. Import from Internet Explorer. Export.
3. Boot into Ubuntu and Import the Exported file?

Or are you unable to boot into Windows, for whatever reason?

---

### Post by AmboyGuy on 2006-01-11
From the Mozillazine Knowledge base :
[http://kb.mozillazine.org/Import_bookmarks#From_Internet_Explorer](http://kb.mozillazine.org/Import_bookmarks#From_Internet_Explorer)

---

### Post by aysiu on 2006-01-11
[QUOTE=AmboyGuy]From the Mozillazine Knowledge base :
[http://kb.mozillazine.org/Import_bookmarks#From_Internet_Explorer](http://kb.mozillazine.org/Import_bookmarks#From_Internet_Explorer)[/QUOTE] "**On Windows,** Mozilla Suite will automatically import Internet Explorer "Favorites" when first installed and whenever you  create a new profile. To manually import your IE Favorites into Mozilla Suite or Firefox, first you have to export them to a file from within IE, then use the Mozilla Suite or Firefox Bookmarks Manager to import that file."

So to those who want to import... can you boot into Windows?

---

### Post by AmboyGuy on 2006-01-11
I'd just export the IE bookmarks as an HTML file to a floppy and then import them into Linux Firefox with the floppy. 
That way you even have a backup of your bookmarks for both windows & linux. (for those rare occasions when your cleaning up your files and delete something you need ) (of course I've never done that ... )

---

### Post by MindFork on 2007-06-13
> **AmboyGuy said:**
> From the Mozillazine Knowledge base :
[http://kb.mozillazine.org/Import_bookmarks#From_Internet_Explorer](http://kb.mozillazine.org/Import_bookmarks#From_Internet_Explorer)
That did the trick for me.  Thanks.

---

