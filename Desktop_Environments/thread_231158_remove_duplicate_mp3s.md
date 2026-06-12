---
title: "remove duplicate mp3s"
date: 2006-08-07
forum: Desktop Environments
---

### Post by rkakkar on 2006-08-07
Certain music players have the ability to weed out duplicate mp3s on the hdd. Any recommendations for any software which removes duplicate mp3s?

---

### Post by peabody on 2006-08-07
> **rkakkar said:**
> Certain music players have the ability to weed out duplicate mp3s on the hdd. Any recommendations for any software which removes duplicate mp3s?

No, but I can recommend the following python script I wrote:

```
[font="monospace"]
#!/usr/bin/python
import os, filecmp, glob

def find_duplicates(folder):
    """Constructs a list of files that are the same in the given folder"""
    music_files = (glob.glob(os.path.join(folder, "*mp3"))
                   + glob.glob(os.path.join(folder, "*MP3")))
    music_files.sort()
    files2delete = []
    for i in range(len(music_files)):
        for music_file in music_files[i + 1:]:
            if filecmp.cmp(music_files[i], music_file):
                if music_file not in files2delete:
                    files2delete.append(music_file)
    return files2delete
    
if __name__ == '__main__':
    files2delete = find_duplicates('.')
        
    for each_file in files2delete:
        print "Deleting %s" % each_file
        os.unlink(each_file)

[/font]
```

Copy and paste into gedit, save as dups.py, and chmod +x dups.py from the shell to make executable, then run the script from within the folder you wish to delete duplicates from like the following:

mv dups.py mp3folder/
cd mp3folder
./dups.py

MAKE A BACKUP BEFORE DOING THIS!  I make no gaurantees and am not responsible for problems.  The script works for me.

---

### Post by rkakkar on 2006-08-07
Hey man,

Couple of things.

1) If i'm not mistaken this program checks for identical file names right? its not possible for two identical filenames in the same folder.

2) Also, what about mp3s in subfolders?

Thanks. Appreciate the help.

---

### Post by peabody on 2006-08-07
> **rkakkar said:**
> Hey man,

Couple of things.

1) If i'm not mistaken this program checks for identical file names right? its not possible for two identical filenames in the same folder.

2) Also, what about mp3s in subfolders?

Thanks. Appreciate the help.

You are mistaken, it compares files by looking at inodes and seeing if they match.  Of course you can't have duplicate names within the same folder!

I could rewrite it to recurse folders.  I'll let you know if I get around to it.

---

