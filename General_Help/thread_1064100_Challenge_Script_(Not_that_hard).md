---
title: "Challenge Script (Not that hard)"
date: 2009-02-08
forum: General Help
---

### Post by mlissner on 2009-02-08
I'm trying to find all of the directories on my system that:
 - Only contain one file
 - Where that one file is a png file

Once those files are found, the directory and the png inside it should be deleted.

I put my mind to it for a bit, but I haven't figured it out yet. Any takers for the challenge?

The reason I want to do this is because Amarok creates a directory for each album, with the png file for the cover art in the directory. Later, when you delete the music itself, the png and the directory itself stick around, making a mess.

Some clues from my research:
This deletes all empty directories:
  - find $searchdir -empty -print0 | xargs -0 rm -rf

This finds all png files: 
 - find $searchdir -name "*.png" -type f 

But how to find directories with only one file, being a png?

---

