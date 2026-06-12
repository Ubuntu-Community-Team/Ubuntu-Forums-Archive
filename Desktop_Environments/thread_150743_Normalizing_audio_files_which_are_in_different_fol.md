---
title: "Normalizing audio files which are in different folders"
date: 2006-03-26
forum: Desktop Environments
---

### Post by Ferio on 2006-03-26
Hi, 

I have a Music folder, with many Bands folders inside it, and Disc folders inside every Band folder. I wanna use normalize-mp3 with all the files in every Disc folder, and I wanted to know if there is a way to run a command to do it. I'm almost sure it exists, but I'm not so experienced with command line. Any help will be useful, thanks!

---

### Post by jpkotta on 2006-03-26
I think something like this will work.  I have not tested it thoroughly.  Backup your music before trying it.

```

for dir in `find ~/Music -type f -iname '*.mp3' -exec dirname '{}' \; | uniq` ; do
    (cd "$dir" ; normalize *.mp3)
done

```

find is your friend.

---

### Post by Ferio on 2006-03-26
I think it works like a charm, I've tested it and it seems to do what I want; I'll try it tomorrow with my Music folder, let's see what happens. Thank you very much!

---

