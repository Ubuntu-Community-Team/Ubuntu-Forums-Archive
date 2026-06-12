---
title: "too long file/foldernames"
date: 2005-12-15
forum: General Help
---

### Post by //RF on 2005-12-15
I dont know if this is right place to post this put posted it anyway, kill me if i was wrong :)

Straight to my problem,

i have lots of mp3 files (~16000) and i want to upload them to my xbox via gftp, but many of them has too long file/foldernames. Filenames over 42 chars are not supported so it just stops the uploading when first file with over 42 chars comes to queue.

Is there any easier way than manual for cutting all the files/foldernames with over 42 chars to max 42 chars, like a bash script for example?

//RF

---

### Post by schilcha on 2005-12-15
Here's a bash-loop that should do it. It assumes that the first 38 letters of the filenames are unique (otherwise you'd need to test if a file with the new name already exists and make a variation to generate a unique name.
```

mkdir /tmp/transfer.mp3s
for f in `ls *.`
do
  newname=`echo "$f" | sed -e "s/^\(.\{38\}\).*\(.mp3\)/\1\2/"`
  cp $f /tmp/transfer.mp3s/$newname
done

```

PLEASE NOTE: I haven't really tested it, so try it before in a safe place;-)

---

### Post by //RF on 2005-12-15
[QUOTE=schilcha]Here's a bash-loop that should do it. It assumes that the first 38 letters of the filenames are unique (otherwise you'd need to test if a file with the new name already exists and make a variation to generate a unique name.
```

mkdir /tmp/transfer.mp3s
for f in `ls *.`
do
  newname=`echo "$f" | sed -e "s/^\(.\{38\}\).*\(.mp3\)/\1\2/"`
  cp $f /tmp/transfer.mp3s/$newname
done

```

PLEASE NOTE: I haven't really tested it, so try it before in a safe place;-)[/QUOTE]
Thanks a lot mate, it works like a charm :D

---

### Post by //RF on 2005-12-15
...except noticed that i can't really use it like i wanted. I tested it to single mp3 file and it worked. Thing is that all my music are in different folders and some of those folders even have 2 more folders inside them (CD1 & CD2).

So, i tried with my 3 week linux knowledge to copy the mp3 files to different folder but im really not that familiar with console, tried also copying the files from Gnomes own search tool (searched *.mp3 in my HDD1), which apparently doesnt work :D 

Is there a command which can copy every mp3 file, meaning scanning every folder like inside my HDD1?

Thanks again,

//RF

---

### Post by schilcha on 2005-12-16
[QUOTE=//RF]Thing is that all my music are in different folders and some of those folders even have 2 more folders inside them (CD1 & CD2).
[/QUOTE]

Ok, use find instead of ls. I also included a crude workaround to deal with filenames containing spaces...
I tried it with some files here. It worked ok up to the point, where two files result in the same truncated name (i.e. the first 38 characters are equal). One could 
add something like "if [  -e $newname ]; then newname="someothername";fi".

```

mkdir /tmp/transfer.mp3s
for f in `find ./ -name \*.mp3 | sed -e "s/ /__SpAcE__/g"`
do
  f=`echo "$f" | sed -e "s/__SpAcE__/ /g"` 
  newname=`basename "$f" | sed -e "s/^\(.\{38\}\).*\(.mp3\)/\1\2/"`

  # uncomment the following 2 lines to copy the dir-structure
  #mkdir -p "/tmp/transfer.mp3s/`dirname "$f"`/"
  #cp "$f" "/tmp/transfer.mp3s/`dirname "$f"`/$newname"

  cp "$f" "/tmp/transfer.mp3s/$newname"
done

```

---

### Post by //RF on 2005-12-16
[QUOTE=schilcha]Ok, use find instead of ls. I also included a crude workaround to deal with filenames containing spaces...
I tried it with some files here. It worked ok up to the point, where two files result in the same truncated name (i.e. the first 38 characters are equal). One could 
add something like "if [  -e $newname ]; then newname="someothername";fi".

```

mkdir /tmp/transfer.mp3s
for f in `find ./ -name \*.mp3 | sed -e "s/ /__SpAcE__/g"`
do
  f=`echo "$f" | sed -e "s/__SpAcE__/ /g"` 
  newname=`basename "$f" | sed -e "s/^\(.\{38\}\).*\(.mp3\)/\1\2/"`

  # uncomment the following 2 lines to copy the dir-structure
  #mkdir -p "/tmp/transfer.mp3s/`dirname "$f"`/"
  #cp "$f" "/tmp/transfer.mp3s/`dirname "$f"`/$newname"

  cp "$f" "/tmp/transfer.mp3s/$newname"
done

```[/QUOTE]

Yep, now seems to work, at least its doing something. :)
I'm glad that people are very helpful here in this great community.

Thanks again schilcha!

---

