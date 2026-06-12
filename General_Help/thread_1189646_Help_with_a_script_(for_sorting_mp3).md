---
title: "Help with a script (for sorting mp3)"
date: 2009-06-16
forum: General Help
---

### Post by asphixmx on 2009-06-16
Hi, I got a script for sorting mp3. I have lots of mp3 in one folder, and want them organized (all the tags are ok). It gets the Author,Title,Album & Genre from the mp3 tag. Then it creates Folders and organize the files like this: GENRE/AUTHOR/ALBUM/author-title.mp3 My problem is that the script eliminates the spaces in the file/folder name and the GENRE has strange characters at the end. I know it is because of the awk command, but since I am a newbie I dont know how to use it correctly. Any one could help? Thanks. My script is this:

#!/bin/bash
TITLE="`id3tool "$1" | grep '^Song Title:' | awk '{ for (i=3;i<=NF;i++) { printf $i } }'`"
ARTIST="`id3tool "$1" | grep '^Artist:' | awk '{ for (i=2;i<=NF;i++) { printf $i } }'`"
ALBUM="`id3tool "$1" | grep '^Album:' | awk '{ for (i=2;i<=NF;i++) { printf $i; } }'`"
GENRE=" `id3tool "$1" | grep '^Genre:' | awk '{ for (i=2;i<=NF;i++) { printf $i } }'`"

install -D "$1" /home/asphix/Public/prueba/"$ARTIST"/"$ALBUM"/"$ARTIST - $TITLE".mp3

---

### Post by ezramorris on 2009-06-17
> **asphixmx said:**
> Hi, I got a script for sorting mp3. I have lots of mp3 in one folder, and want them organized (all the tags are ok). It gets the Author,Title,Album & Genre from the mp3 tag. Then it creates Folders and organize the files like this: GENRE/AUTHOR/ALBUM/author-title.mp3 My problem is that the script eliminates the spaces in the file/folder name and the GENRE has strange characters at the end. I know it is because of the awk command, but since I am a newbie I dont know how to use it correctly. Any one could help? Thanks. My script is this:


Hi, if your mp3 files have ID3 1.x tags, you might find mp3info is easier to use, as you could just do:
```
install -D "$1" "/path/to/your/music/folder/"$(mp3info -p '%g/%a/%l/%a - %t.mp3' "$1")
```

I've used $() instead of `` (backticks) because backticks are now deprecated.

If that doesn't work, or you don't want to install it, sed would probably be easier to use sed instead of awk.
```
TITLE=$(id3tool "$1" | grep '^Song Title:' | sed 's/^.*\t//g')
...etc...
```
That basically removes everything from the start of the line to the tab(s).

Hope this helps.

---

### Post by asphixmx on 2009-06-17
Thank you very much ezramorris!! Worked fine with "sed", as you said. Now my script works! I new about "sed", but I really didn't understand the syntaxis, looked everywhere but it is confusing (at least for me). I am learning :)

---

### Post by ezramorris on 2009-06-17
> **asphixmx said:**
> Thank you very much ezramorris!! Worked fine with "sed", as you said. Now my script works! I new about "sed", but I really didn't understand the syntaxis, looked everywhere but it is confusing (at least for me). I am learning :)

See `man sed' if you haven't already.

Sed is actually a scripting language of its own. Its most commonly used command is
```
s/regex/replacement/
```
Which is what I've used here.

In this case I used the regex (regular expression)
```
^.*\t
```
which means "match the start of the line" (^), "followed by any character" (.) "any number of times" (*), "followed by a tab character" (\t).

The "g" after s/// means repeat it again if it's found on the same line. You don't actually need it here, but I wasn't thinking and did it out of habit. It does nothing in this case though.

So,
```
sed 's/^.*\t//'
```
would be fine.

---

### Post by ghostdog74 on 2009-06-18
> **asphixmx said:**
> Hi, I got a script for sorting mp3. I have lots of mp3 in one folder, and want them organized (all the tags are ok). It gets the Author,Title,Album & Genre from the mp3 tag. Then it creates Folders and organize the files like this: GENRE/AUTHOR/ALBUM/author-title.mp3 My problem is that the script eliminates the spaces in the file/folder name and the GENRE has strange characters at the end. I know it is because of the awk command, but since I am a newbie I dont know how to use it correctly. Any one could help? Thanks. My script is this:

#!/bin/bash
TITLE="`id3tool "$1" | grep '^Song Title:' | awk '{ for (i=3;i<=NF;i++) { printf $i } }'`"
ARTIST="`id3tool "$1" | grep '^Artist:' | awk '{ for (i=2;i<=NF;i++) { printf $i } }'`"
ALBUM="`id3tool "$1" | grep '^Album:' | awk '{ for (i=2;i<=NF;i++) { printf $i; } }'`"
GENRE=" `id3tool "$1" | grep '^Genre:' | awk '{ for (i=2;i<=NF;i++) { printf $i } }'`"

install -D "$1" /home/asphix/Public/prueba/"$ARTIST"/"$ALBUM"/"$ARTIST - $TITLE".mp3

you don't have to use grep + awk. If there is awk, no need for grep. Just one awk program will do
```

#!/bin/bash
id3tool "$1" | awk 'BEGIN{
 FS=":";q="\047"
 path=" /home/asphix/Public/prueba/"
}
!/^$/{
  gsub(/^[[:blank:]]+|[[:blank:]]+$/,"",$2)  
  info[$1]=$2   
}END{
    cmd = "install -D "q info["Filename"] q path info["Artist"]"/"info["Album"]"/"info["Artist"]"-"info["Song Title"]
    print cmd
    #system(cmd) #uncomment to use
}'

```

---

### Post by ghostdog74 on 2009-06-18
> **ezramorris said:**
> See `man sed' if you haven't already.

Sed is actually a scripting language of its own. Its most commonly used command is
```
s/regex/replacement/
```
Which is what I've used here.

though you can call it "scripting language" as its supposed to be turing complete as well, you seldom use it to do actual programming.

> 
So,
```
sed 's/^.*\t//'
```
would be fine.
what if the song title contains multiple tabs ?? 

> 
sed would probably be easier to use sed instead of awk

on the contrary, you might find working with fields and delimiters is easier than constructing regex.

---

### Post by asphixmx on 2009-06-22
Wow... sincerly I didn't understand the awk program. It is in a much more advanced level I am right now... but thanks anyway. I have to study more! :)

---

