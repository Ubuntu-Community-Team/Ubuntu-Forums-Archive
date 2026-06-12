---
title: "Automatic Linking"
date: 2009-02-24
forum: General Help
---

### Post by Armaron on 2009-02-24
I've got both Windows XP and Ubuntu 8.10 set up on my pc. I used Win a long time before Ubu. So I set up a seperate partition for My Documents. On that NTFS partition are all my music and films, etc. And I want to keep downloading stuff into those folders. But I like to have easy access to my files.

Is there a way to let Ubu put a link in my /home/Armaron/Music folder each time I save a file in say My Music folder?

---

### Post by heindsight on 2009-02-24
You could just make /home/Armaron/Music a link to wherever "My Music" is.

For example, if your NTFS partition is mounted at /media/Documents and your "My Music" directory is at /media/Documents/My Music, you could delete /home/Armaron/Music (back up anything in there that you want to keep first) and then replace it with a link to /media/Documents/My Music:

```
rm -R /home/Armaron/Music
ln -s /media/Documents/My\ Music /home/Armaron/Music
```

---

### Post by unutbu on 2009-02-24
Yes, I could write such a script, but wouldn't it be easier to copy all the files into "My Music" folder (on the NTFS partition) and then make /home/Armaron/Music a symlink to "My Music"?

For example, if "My Music" is mounted at /media/Windows/ then 
```

mv ~/Music/* "/media/Windows/My Music"     # Move files to My Music
rmdir ~/Music                              # Remove the empty ~/Music directory
ln -sf "/media/Windows/My Music" ~/Music   # Symlink ~/Music to My Music

```

---

### Post by Armaron on 2009-02-24
Haha, dumba$$ me. That would make a lot more sense. :p

Thanks for the quick replies!

---

