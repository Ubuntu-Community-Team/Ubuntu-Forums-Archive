---
title: "Bash command: 'for'"
date: 2009-06-21
forum: General Help
---

### Post by Sutur on 2009-06-21
Hi Guys,

My goal is to convert all FLV files in a folder and it's subfolders to AVI using the below command:

```
ffmpeg -i video.flv video.avi
```

Trouble is I want to issue the above command to a folder recursively and repeat this command to all flv files found within them, using their original filenames.

I know the 'for-in-do' trick is the key, I just need some help implementing it...

---

### Post by lloyd_b on 2009-06-21
If you want it to be recursive, then you'll probably need to use "find" to get the file names:```
IFS=$'\n'
for FILE in `find . -name "*.flv" -print`; do
   ...
done
```(NOTE: Those are "backtics" (above the tab key on US keyboards) around the find command, NOT single quotes).
The "IFS=$'\n'" changes the "field separator" used by the for loop to be just a newline - normally, it's space, tab, and newline, but if you have spaces in the filenames, the for loop would be erratic.

Once you have the filename, all you need to do is replace ".flv" with "avi" to generate the new filename, and then call the conversion.  The replace can be done using bash's string handling:```
NEWFILE="${FILE%.flv}.avi"
```(The "${FILE%.flv}" trims the extension from FILE, and the ".avi" adds the new extension).

Hope this gives you some good starter info.  I'd suggest at least trying to read bash's man page ("man bash" in a terminal window), but it can be kinda tough to follow at times.

Lloyd B.

---

### Post by ghostdog74 on 2009-06-21
don't have to specifically change the IFS. 
```

find . -name "*.flv" -print | while read FILE
do
  ...
done  

```

---

### Post by paperplate9 on 2009-06-21
But he wants to use the 'for' internal ;)

---

### Post by ghostdog74 on 2009-06-21
> **paperplate9 said:**
> But he wants to use the 'for' internal ;)

for and while read are both internal. changing IFS is ok, but remember to change it back after use. (that's why i myself prefer not to meddle with it)

---

