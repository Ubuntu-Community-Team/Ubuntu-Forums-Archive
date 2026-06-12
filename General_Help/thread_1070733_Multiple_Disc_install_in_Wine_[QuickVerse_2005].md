---
title: "Multiple Disc install in Wine [QuickVerse 2005]"
date: 2009-02-15
forum: General Help
---

### Post by zachthejones on 2009-02-15
I'm trying to install a program (QuickVerse 2005) in wine. The installer seems to work fine, but it requires 2 discs for the installation, and when it prompts me to insert the second disc, ubuntu/gnome/nautilus won't eject the disc because it says a program is using the drive. I had to choose to cancel the installation at that point to stop the program so I could insert the 2nd disc. When I did, of course, nothing happened. So I tried to run the "disc2.exe" through wine - but nothing happens.

Anyone know how to do a multiple disc installation in Wine? The install seems to be going rather perfectly - it just can't finish...

---------------------

And why QuickVerse? Well, this is a gift from a few years ago, but it is an expanded edition, which includes many resources not available (at least in my searching) in Gnomesword or eSword. I understand that eSword can read the books from it in the STEP reader, but I want to be able to access the files in the native Bible program, search and cross-reference between them - and as far as I can tell, I can't install the resources from my QuickVerse discs into eSword (but if anyone knows how to do this, please let me know!!!!

---

### Post by biovore on 2009-02-17
I have had this problem before..   I cheated.
I copied the contents of both discs into 1 directory on my harddisc and did the install from there.

You "could" in theory use a paperclip to force the disc to eject and just slip in the new disc. (sometimes works..)

---

### Post by jamescchandler on 2009-06-08
I have heard that you could open a second terminal and type
"wine eject".  I've not tried it myself but it seems it would be easier than the paper clip. :) 

Jim

---

### Post by zachthejones on 2009-06-08
yeh...I opted out of the paper clip alternative...I tried as biovore suggested and copied all the contents of both discs into one folder. That seemed to work - at least the install finished (and it may have gone faster...). Unfortunately the program still didn't work - but I think that had less to do with the install and more to do with me trying to run it in wine (and maybe using an older computer...).

---

