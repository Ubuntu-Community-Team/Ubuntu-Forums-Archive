---
title: "HELP! Lost all my music..."
date: 2005-07-30
forum: Desktop Environments
---

### Post by royg1234 on 2005-07-30
I was listening with amaroK, then I stopped it (but left it open) and did something else.  When I came back my library was empty, and the folder (/mnt/files/music -- a fat32 partition) isn't there anymore.

But my drive's just as full as before, so I HOPE it's still there.  I booted into Windows XP and into Suse, and neither one saw it either.  Any ideas?

---

### Post by amohanty on 2005-07-30
Did you try to remount it manually??

AM

---

### Post by royg1234 on 2005-07-30
yeah.  It's still not there.  Even when I reboot into XP, Windows doesn't see the music folder. :-(

---

### Post by royg1234 on 2005-07-31
more details:

NB The partition's other files and folders are still there... the only one that's missing is the music folder.

NB no space was freed on the drive.  i.e. the lost folder is still taking up space (a LOT of space).

What might have caused it is this:  I had  playlist in amaroK (hooked up to mySQL).  I changed some of the filenames (*.m4a --> *.mp4) via Nautilus.  And when amaroK got to those songs, it just pooped out and decided to "delete" the whole folder???  NB these files were a couple levels below the music folder, but the whole music folder was still lost.

What steps should I take to recover?  I feel like the music is still in the drive somewhere.  :???:

---

### Post by royg1234 on 2005-07-31
LOL.  False alarm.  I did a dosfsck -l and it showed me that the music was just moved to another folder (how, I don't know). \\:D/

---

