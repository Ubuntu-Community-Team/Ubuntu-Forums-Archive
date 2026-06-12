---
title: "I'm trying to use bash to move a lot of files at once"
date: 2008-12-26
forum: General Help
---

### Post by holdie on 2008-12-26
So I'm trying to run this bash scripts to do a mass-move/rename for me.  Basically, I have a bunch of different folders with a file called "torrent" in them.  I want all the individual files to be aggregated in one folder (Desktop/torrents) elsewhere, so I need to change the name for each one.

I'm trying to accomplish this with the following code
```

#!/bin/bash

j = 0

for oldfile in `find -name torrent`; do
	let "j += 1"
	cp $oldfile "/home/chris/Desktop/torrents/$j.torrent"
done


```

But I'm getting the error 8: let: not found

I've used the same "find" command with just the command line, and it brings up everything fine, so maybe it has something to do with "j"...?

I'm pretty new to the bash (if that's not obvious :P ) so I'd appreciate any help you guys can give

thanks

---

### Post by Ahadiel on 2008-12-26
Instead of
```
let "j += 1"
```
try
```
$j=$j+1
```

edit: it may just be j=$j+1

---

### Post by kaibob on 2008-12-26
When creating a variable, I don't believe there can be a space between the name of the variable and the equal sign. I think the following will do what you want. You may want to change the directory and -name in the find command. 

```
#!/bin/bash
j=1
find . -name '*torrent*' -type f | while read FILE ; do
cp "$FILE" "/home/chris/Desktop/torrents/$j.torrent"
j=$(($j+1))
done
```

---

### Post by holdie on 2008-12-26
haha so I tried changing it to j=$j+1 and it started tacking "+1" on the end of each filename, so by the end I got something like 1+1+1+1+1+1+1....torrent and it returned a file too long error

anyways, I figured it out, I found a tutorial (back from 2001!) that said arithmetic operations need to be enclosed in parentheses and prefaced with a $

eg: q = $(($q + 4))

anyways, here's the code that worked for me if anyone is curious

```
#!/bin/bash

j=0

for oldfile in `find -name torrent`; do
	j=$(($j+1))
	cp $oldfile "/home/chris/Desktop/torrents/$j.torrent"
done

```

---

