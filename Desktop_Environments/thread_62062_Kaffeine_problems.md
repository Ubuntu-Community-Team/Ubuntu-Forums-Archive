---
title: "Kaffeine problems"
date: 2005-09-03
forum: Desktop Environments
---

### Post by ManLord on 2005-09-03
When I select open file in kaffeine, and navigate to my external harddisk and open a file, kaffeine tells me that I cannot open file from external media. But when I navigate to the same folder with konqueror and click the file there, it opens. 
 
So apparently it can play files from external media. Can't kaffeine just open the file in the first example in the way it opens it in the second example?? 
 
 
Also recently (maby after installing KDE 3.4.2 and the following noathun maybe?) when I click a file in the konqueror, kaffeine opens ALL the videofiles in this folder, and starts with the first, every time. No matter which one I select.

---

### Post by daller on 2005-09-03
Please post the path!

---

### Post by ManLord on 2005-09-03
Like this for example:
/media/sda6/Video/Trailere/hl2aftermath_ot_pc_080905.mpg

This file opens if I select open url, and type in this (but that's ofcourse not something that's easy or convenient to do) If I select open file and select the same file, then it says I cannot select external media.

It seems that when I click the file in konqueror, then the command "kaffeine %U" get's started. Thus making kaffeine open the file as an url, which is the same thing as select url and type it in. 

This is not a big problem, because I can always start it from konqueror.. but it's anoying..


This is also the problem I have with opening files in konqueror, some file types don't open in kaffeine. I then select "open with" and select kaffeine from the menu then the file opens. If I just click the file then I get an error message saying: "KDEInit could not start «/media/sda6/Video/Trailere/hl2aftermath_ot_pc_080905.mpg»."

I guess it's because in the "open with" menu, there is an entry that says "kaffeine" but with no icon, if I select this I get the same error. Another there also says kaffeine, this works... 

But if I select "open with" and "other", select kaffeine and "remember file assosiation" it opens ONCE, but the next time it try to opens it with the old one... ](*,)

---

### Post by ManLord on 2005-09-03
Is there a way to remove the "kaffeine entry with no icon" from the open with menu?

---

### Post by gnutux on 2005-09-03
well, try to download xine-ui for now, it should hold in until a person that knows the ins and outs of Kaffeine (which I don't) to answer you.

gnutux

---

### Post by daller on 2005-09-14
You can modify the "Open with" in kcontrol...

Go to "KDE components" -> "File associations"

The rest should be pretty self-explanatory

Please post if you have ANY problems...

---

### Post by gingermark on 2005-09-14
When you are trying to open the file in Kaffeine, are you actually accessing it as "/media/sda6/Video/Trailere/hl2aftermath_ot_pc_080905.mpg" or are you selecting your external harddrive?

To put things simply if you have a second harddrive, say "hdb", and you've mounted that as /media/hdb, and you have a file called "film.avi" on the drive you wish to open, then Kaffeine would be able to open "/media/hdb/film.avi" but won't manage to open "media:/hdb/film.avi".

So, depending on where your mount point is, you're probably looking at a couple of extra clicks from the root directory to get where you're going, which isn't too bad.

Sure, Konqueror can access the data directly off a mounted hard drive, but if you want to edit or delete anything you'd still have to access it via its mount point directory.

---

### Post by ManLord on 2005-09-16
I solved the first one.
This is the ramaining problem i now have:
----------
Also recently when I click a file in the konqueror, kaffeine opens ALL the videofiles in this folder, and starts with the first, every time. No matter which one I select.
-----------

And it doesn't matter if I open it from /media/sda6 or media:/sda6.

---

### Post by daller on 2005-09-19
This has been fixed in Breezy - go ahead and upgrade, everything works perfect on the pc's i've installed it on so far!

Good luck!

---

