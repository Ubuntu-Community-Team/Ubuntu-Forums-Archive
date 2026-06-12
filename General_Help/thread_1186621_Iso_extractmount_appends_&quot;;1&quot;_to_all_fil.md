---
title: "Iso extract/mount appends &quot;;1&quot; to all filenames"
date: 2009-06-13
forum: General Help
---

### Post by oneindelijk on 2009-06-13
Hi, 

I believe this is a known issue as I've seen this in ubuntu 8.04, 8.10
and now in Jaunty I'm still having this issue, but I don't know how to look for in in google (even with quotemarks only result for "1" showed up):-D
When I either mount or extract a iso file (probably only windows based cd's), all files get ;1 appended.
Has this something to do with the iso96--- standards or something ?
All help much appreciated !!

regards
Sam

---

### Post by mc4man on 2009-06-13
I've never seen that on a mounted .iso but certainly have when viewed and or extracted with the default archive manager (file-roller

peazip doesn't show the same behavior

---

### Post by ajgreeny on 2009-06-13
You must be doing something different to me.  When I either mount or open an iso file in archive manager, I do not get the appended 1 before each file name.  What sort of iso are you dealing with?  The only ones I have are iso files of linux distros which I have downloaded.

---

### Post by mc4man on 2009-06-13
It would happen with a video iso and a quick look suggests many data iso's.
see screen (peazip #3

---

### Post by oneindelijk on 2009-06-14
I tried it with an Office 2007 cd. 
So it's the archive application that causes this.
Maybe it has something to do with the Joliet 9660 standard ?
I wouldn't know how to check which standard the cd is made in...

Or are these screenshots from peazip ?

---

### Post by murphykieran on 2009-06-14
I'm having the exact same problem with ISOs of Windows software or games.  My DVD drive is bust so I'm trying to see if I can bypass it temporarily by mounting or using ISOs, but the filenames are all screwed up whether I mount it or extract the files to a folder.  Every files has ;1 attached to the end so SETUP.EXE becomes SETUP.EXE;1

---

### Post by mc4man on 2009-06-14
> Or are these screenshots from peazip ? 

screens 1 and 2 are from the default archive manager (file-roller) 
screen 3 is same iso as screen 2 but using peazip (no ;1 with peazip

---

