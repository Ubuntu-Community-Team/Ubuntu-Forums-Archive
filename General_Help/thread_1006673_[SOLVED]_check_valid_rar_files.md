---
title: "[SOLVED] check valid rar files"
date: 2008-12-09
forum: General Help
---

### Post by Kissell on 2008-12-09
I have a folder of over 100 rar archives, each containing files over 4GB in size.  

It's recently come to my attention that some of my rar archived files in this folder are no good when I go to extract them... it says the header is corrupt, my guess is someone turned off the computer while they were being created...  but most of the archives are good.

I'd like to test each file, to verify it will open, if it'll open then it'll probably extract the contents.  But I don't want to manually click on each file to open it.  I'm mean, we're talking hundreds of compressed gigs here, so this is going to take forever.  

I'd like to just script it, so from the command line i can run something and come back a day later and see the results...  I just want to know if any of the remaining files are also corrupt, as I've recently found 2 that were.  Anyone know how to do this?

---

### Post by binbash on 2008-12-09
go to the directory where you rar files located , then unrar t *.rar

---

### Post by Kissell on 2008-12-09
thanks

---

