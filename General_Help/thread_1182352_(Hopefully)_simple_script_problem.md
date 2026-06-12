---
title: "(Hopefully) simple script problem"
date: 2009-06-08
forum: General Help
---

### Post by nmccrina on 2009-06-08
Hi guys!

I'm trying to backup my music onto an external hard drive using a bash script. The music is stored in one directory, with each album in its own subdirectory. Here is the script:

```

#!/bin/bash

for file in /home/nfm/docs/music/*
do
	album=${file:21} # This gets just the album name by chopping off
                         # the /home/nfm... part.
	target="/media/disk/music/$album"
	if [ -e "$target" ]; then # Check to see if the target already 
                                  # exists
		echo "/media/disk/music/$album exists..."
	else
		cp -rv $file "$target"
	fi
done

```

The problem is that it only works for album names with no spaces. If the album name has a space, it says '/media/disk/music/album/name is not a directory'. How can I force it to create a directory with a space in the name?

---

### Post by synapsys on 2009-06-08
Have you tried....
```
target="/media/disk/music/$album*"
```

---

### Post by nmccrina on 2009-06-08
:-k

That was strange. The best way to describe what happened is with an example. It copied the files in "/home/nfm/docs/music/90125/" to "media/disk/music/90125*/". However, it tried and failed to create "media/disk/10,000 Days*/"

I'm thinking about giving in and using Nautilus to drag and drop the directories over. ](*,)

Anyway, if I'm being "by the book" I should not have spaces in directory or file names, right? It just looks bad having "A_Momentary_Lapse_of_Reason/02_-_Learning_To_Fly.flac". Well, actually, I could live with that :) I think I'll just write a script to replace spaces with underscores, and try it again. ):P

---

