---
title: "How do I read QuickVerse 2005 STEP books in eSword?"
date: 2009-03-28
forum: General Help
---

### Post by zachthejones on 2009-03-28
I've got QuickVerse 2005 installed through Wine, but it freezes when I try to start it. I did get eSword installed successfully, and I understand you can use it's STEP reader to read books from Quickverse, but I can't get it to work.

When I open the STEP reader in eSword it is looking for an *.ini file, but there are none in the QVBooks folder. Do you use the installed files or the files straight from the disc?

There is a specific (and expensive) commentary on my QuickVerse program I need to access - any help would be awesome!!!!

(and if anyone has gotten QuickVerse to work on Ubuntu - please tell!!!!)

---

### Post by zachthejones on 2009-03-28
Okay, right after I posted that, I figured it out:

when you click on the "open" icon, change the file type it is searching for to the book.dat format. That is apparently what QuickVerse uses. The files are located in the hidden wine folder (make Nautilous so it can view hidden files, and go to your home folder, then go to the .wine folder). In there you go to "drive_c", then "Program Files", then "QuickVerse9" (or whatever version you have), then finally to the QVBooks folder. In this folder all your books are separated into folders. Have fun figuring out what the abbreviated folder names stand for!!!

I had to copy the "QVBooks" folder to another place because eSword won't recognize the hidden folders. I think I might rename the book folders in their full title so I can know what I'm looking at later...

(Still looking for someone who knows how to get Quickverse working on Ubuntu...)

---

