---
title: "Copying one file to multiple locations"
date: 2006-08-25
forum: Desktop Environments
---

### Post by Freelance Physicist on 2006-08-25
Quick background: My laptop is dual-boot Windows and Ubuntu with a shared fat32 partition where I keep all of my documents which is mounted as ~/Documents.  Many of the folders and subfolders contain a Thumbs.db file in which Windows stores thumbnails for pictures in that folder.  These are hidden by default in windows but visible in Ubuntu.

I wanted to create a .hidden containing 'Thumbs.db' and 'desktop.ini' in ~/Documents and in every subfolder.  After doing quite a bit of research, I decided to create a .hidden file with the two files mentioned above in gedit.  I then opened a terminal and ran this:

```
~$ find ~/Documents -print0 -type d -iname '*' | sed 's/$/\/\.hidden'/ | xargs -i -0 -n1 -t cp '.hidden' {}
```

What I thought this would do:
(1) find and list every subfolder directory (e.g. '/home/mark/Documents/Pictures')

(2) append '/.hidden' to the end of every directory (e.g. '/home/mark/Documents/Pictures/.hidden')

(3) copy the .hidden file to the newly created target: '/home/mark/Documents/Pictures/.hidden'

What in fact happened was that not only was the .hidden file copied to the new directory, but every file was being replaced with a copy of the original .hidden--pictures, videos, downloads, etc.  Luckily, I had put in the -t option in xargs so I could see this happening and halt the process before too much damage was done.  Also luckily, I had backups ready and did not lose any critical data (just 6 gigs of porn ](*,) ).

Anyway, what was wrong with my command?  I tried running it without piping to xargs and the result was a list of directories--no files--like I expected.  Why did my command pipe file names as well as directory names to xargs cp?

---

