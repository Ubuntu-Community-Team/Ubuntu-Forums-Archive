---
title: "Help ! My downloads folder is gone ! [Ubuntu 11.10]"
date: 2012-08-03
forum: Desktop Environments
---

### Post by Hantan on 2012-08-03
Hey guys,
              Yesterday after i  booted up, i suddenly got a dialog saying 'you have logged in in a new  language' and asked me whether i should rename /home/ananth to  /home/ananth/Downloads. I said keep old names, but when i checked  there's no Downloads folder ! In cairo dock, where i had the shortcut to  downloads, now shows 'unmounted'. Can someone please let me know how i  can recover it back?

Thanks,
Ananth.

---

### Post by Grenage on 2012-08-03
If the Downloads directory is just a directory (and not a link), can you not simply recreate the directory within Nautilus?  I am guessing that you're after the old contents?

---

### Post by ajgreeny on 2012-08-03
If you know the name of some of the files that are now missing(?) you can possibly find where that folder has gone with the **find** or **locate** commands.

I find the **locate** command easier to use as it requires much less detailed syntax, but first update your filesystem database with ```
sudo updatedb
```then run ```
locate -i <filename>
```using your hopefully remembered filename, which may give you some clue what is going on.

---

### Post by Hantan on 2012-08-03
Yes, i'm after the old contents which have been obliterated ! There's no link, no folder. I had atleast 2 gigs of data inside it :( I checked the space occupied, it shows the same as before. So there was no accidental deletion.

---

### Post by Hantan on 2012-08-03
I did updatedb and then did a locate on a file that should have been there in the Downloads folder, but the search turned up empty.

---

