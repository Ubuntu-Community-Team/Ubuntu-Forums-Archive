---
title: "Identify/Open recovered foremost files"
date: 2009-06-09
forum: General Help
---

### Post by theluddite on 2009-06-09
I had to reinstall Intrepid a while back and have since found out my wife had a very, very, very important text file that wasn't backed up.  I ran foremost on the disk and recovered a bunch of ole files.  **Now how do I find the right one? ** Most of the files I've opened with Openoffice.org writer (that's what she used to create the file) are blank.  My only help is that I know that the file was huge (130 pages of text).  Also, it's very likely that the file was overwritten since I formatted the drive -- **could I still recover an overwritten file**?  I know that secure deletion requires a file to be overwritten several times before it's unrecoverable.  So what should I use to recover overwritten files?

---

### Post by theluddite on 2009-06-16
Can anyone suggest a program to reconstitute/open even corrupted text files?

---

### Post by rbc on 2009-06-16
First of all, thanks for bringing foremost to my attention. I have been playing with it since you first posted. To restore files that have been severely overwritten, you will most likely need a hex editor and rebuild it. Very time consuming, and I have only done it with very small files. May I suggest testdisk/photorec. I have had very good luck with, although as far as I know I was only able to recover files that had been deleted but not yet overwritten. By the way, were able to get foremost to search specifically for .odt files? The literature seems to suggest that, by default, foremost does not search for that type of file. How large a hard drive was it and how much has the computer been used since you reformatted?

---

### Post by theluddite on 2009-06-16
> **rbc said:**
> First of all, thanks for bringing foremost to my attention. I have been playing with it since you first posted. To restore files that have been severely overwritten, you will most likely need a hex editor and rebuild it. Very time consuming, and I have only done it with very small files. May I suggest testdisk/photorec. I have had very good luck with, although as far as I know I was only able to recover files that had been deleted but not yet overwritten. By the way, were able to get foremost to search specifically for .odt files? The literature seems to suggest that, by default, foremost does not search for that type of file. How large a hard drive was it and how much has the computer been used since you reformatted?

Yeah, I found out about foremost in the last edition of 2600.  Thanks for the hex editor suggestion, I'll try GHex or Vim.  Even if I can't rebuild the whole file, I'd like to recover at least part of it.

I tried testdisk but it kept saying the disk was corrupt, maybe I'll try photorec.  I was able to open a couple of deleted text files that were saved with Open Office, so either they were saved as .doc files or foremost does in fact recover .odt.

The harddrive is 260Gb (not including the 60Gb windows partition) and I've filled as much as 40% of it since then.

---

### Post by rbc on 2009-06-16
For what it's worth, here's a link to the document I read to learn about data carving. The down side is that the practice sessions are all done with floppy disks which, obviously, are much easier to work with than a large hard disk.
[http://www.linuxleo.com/](http://www.linuxleo.com/)
Look for the link for the pdf entitled The Beginner's Guide v3.78. It is a starters' how-to for computer forensics. Even if one's goal is not to do forensic work, it is still a great read, and shows just how versatile linux is

---

