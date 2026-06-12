---
title: "How do I search a directories and its subdirectories for certain filetypes then move"
date: 2009-03-03
forum: General Help
---

### Post by Scubdup on 2009-03-03
Sorry for search a basic question, but I just can't find out how to do it.

My mp3 files are all over the place, as are our photos, so I want to find them all, rename them with their directory path, so I don't have the problem of multiple mp3 tracks called "track 01" etc, and then move them into two new directories, "Music", and "Photos".

I've tried using Thunar, GPRename, Metamorphose, Purr and PYRename, but I cannot get these to search subdirectries rather than just the current directory.

As for finding files by filetype, and moving them, I haven't a clue.

Thanks for any help.

---

### Post by Old *ix Geek on 2009-03-03
I'm having a very bad day (I found out this afternoon I have to have brain surgery), so I'm a bit out of it.  I won't try to work out the script for you because I'd probably get it wrong, but basically you can do this with **find** and the **-exec** option.  The general idea would be to do something like:
```
find / -name *.jpg -exec [renaming and copying commands will go here] '{}' \;
```

This will search the entire filesystem for jpegs, then act on each file with the commands you specify.  I'm sure someone else can help with the details.

---

### Post by NikoC on 2009-03-03
Hmmz I just gave this one a try and I think this might work (as an example):

- Start Nautilus
- Go to Home directory
- Ctrl + F
- Search: *.mp3

This will find all files with an mp3 extension in your home folder!

Edit: ignore this one, I missed the renaming part you requested... sorry :(

---

### Post by geirha on 2009-03-03
I'd try with something like this:
```
find -name "*.mp3" -print0 | xargs -0 -- rename -n 's|.*/([^/]+)/(.*)\.mp3|/path/to/Music/$1 - $2.mp3|'
```

Without the -n option to the rename command, that should move and rename each mp3 to /path/to/Music/, with the last directory component added to the filename, so if «find -name "*.mp3"» finds «./The Who - Who's Next/Track 01.mp3», it will be renamed and moved to «/path/to/Music/The Who - Who's Next - Track 01.mp3»

It might need some tweaking, so keep the -n option there at first. With the -n option it will only print what it would've done, but not actually move/rename anything. Changing -n to -v should do the actual moving and renaming.

Make sure you have a backup at hand just in case.

---

### Post by Scubdup on 2009-03-03
Thanks for the swift replies, guys. I'll be giving these a try when I get home tonight.

At the moment I'm more comfortable with GUI solutions like using Nautilus, but I'm starting to realise why people promote the command line so much - it seems incredibly powerful!

Old *ix Geek, wishing you well for the future.

---

