---
title: "Search and Sort Music"
date: 2009-06-23
forum: General Help
---

### Post by adam_kimber on 2009-06-23
Hi.

I was wondering if it possible to search my music directory and then move entire folders to anoter location based on their contents? 

Here is what I want to actually do.

I have a music collection of ripped music over a lengthy period of time. I first started to rip in 128 MP3 (for size reasons). Now that disk drives are huge I am ripping into 228 OGG and am thinking of ripping into FLAC. 

I want to be able to find all the folders with MP3s in, move them to ~/Music/mp3/ and all the folders with oggs in and move them to ~/Music/ogg/. That way I can see what I need to re-rip! Manually going through each folder would take far to long! 

I hope this can be done! :D

---

### Post by geirha on 2009-06-23
How's the music currently organized? Are there several levels of directories (e.g. Artist/Album/Track - Title) or just one (e.g. Artist - Album/Track - Title)?

---

### Post by sedawk on 2009-06-23
It isn't diffcult to do that with a shell script, but you have
to be careful what you do, e.g. you need to split a file's location
into directory and filename to recreate the correct structure on
the target dir, etc.


But there might be an easier solution: rsync

If you have enough space copy the whole stuff to a new directory
(with rsync -av /old/directory/ /new/directory/)
Then delete all wrong files in the new directory, e.g. remove ogg files
from new directory "find /new/directory/ -name \*ogg -print|xargs rm ".
Then try to remove every directory in /new/directory (that will
only delete empty ones) "find /new/directory/ -type d -print|xargs rmdir"
Do this a few times to get rid of empty dirs that only contained empty
dirs in the step before.

Another solution might be to use the "include/exclude" feature of
rsync, so you only include *mp3 or you exclude *ogg.

---

### Post by adam_kimber on 2009-06-23
Unfortunately I currently do not have enought space to use rsync. Did not know it could be used for that! 

I have my music set up as follows ~/Music/Artist/Album/00. Track name.ogg or mp3
Hope that makes sense. 

I know shell scripts are pretty powerful but they can do that? Could you help out? If poss could you break the script down so that I know how its working? 

Thanks!

---

### Post by geirha on 2009-06-23
Ok, here goes. This script will move albums into ~/mp3 if there are any mp3 files in the album dir, or to ~/ogg if there are any ogg files in the album dir.

It assumes that all music under ~/Music is organized as you described.
```

#!/bin/bash

cd ~/Music/
for artist in *; do
    cd "$artist"/
    for album in *; do
        # If any mp3-files in album dir
        if ls "$album"/*.mp3 &>/dev/null; then  

            # Create the artist dir under ~/mp3 if it does not already exist
            [ -d ~/mp3/"$artist"/ ] || mkdir -vp ~/mp3/"$artist"/

            # Move the album
            mv -v "$album" ~/mp3/"$artist"/

        # Else, if any ogg-files in album dir
        elif ls "$album"/*.ogg &>/dev/null; then 

            # Create the artist dir under ~/ogg if it does not already exist
            mkdir -vp ~/ogg/"$artist"/

            # Move the album
            mv -v "$album" ~/ogg/"$artist"/
        fi
    done
    cd ..
    # Attempt to remove artist directory. Will simply ignore it if it's not empty
    rmdir -v "$artist"/
done

```

I commented it a bit, but feel free to ask if some of it is unclear.

It is possible to do this with a few one-liners (involving find) as well, but they'll be a bit complex, so I decided to just do it with a more readable bash script instead.

---

### Post by ghostdog74 on 2009-06-24
```

find /path/to/music -name "*.mp3" -printf "%h\n" |sort -u| xargs -i mv {} /path/to/mp3
find /path/to/music -name "*.ogg" -printf "%h\n" |sort -u| xargs -i mv {} /path/to/ogg

```

---

### Post by geirha on 2009-06-24
> **ghostdog74 said:**
> ```

find /path/to/music -name "*.mp3" -printf "%h\n" |sort -u| xargs -i mv {} /path/to/mp3
find /path/to/music -name "*.ogg" -printf "%h\n" |sort -u| xargs -i mv {} /path/to/ogg

```

That will lose the directory structure though ...

---

### Post by ghostdog74 on 2009-06-24
i just thought OP wants something simple. anyways, its still easy to fix if directory structure is to be maintained :)

---

### Post by adam_kimber on 2009-06-25
Hey thanks guys! I would like to keep it simple but I would also like to keep the directory structure. :D 

ghostdog - I can understand most of what your one script does, though I am at a loss to what the -printf "%h\n" |sort -u section does. Could you explain?

Thanks for your help!

---

### Post by ghostdog74 on 2009-06-25
> **adam_kimber said:**
> 
ghostdog - I can understand most of what your one script does, though I am at a loss to what the -printf "%h\n" |sort -u section does. Could you explain?

Thanks for your help!

check the find man page under -printf. check the sort man page for -u option and what it does. simple?

---

### Post by adam_kimber on 2009-06-25
Ah yes. Cheers!

---

