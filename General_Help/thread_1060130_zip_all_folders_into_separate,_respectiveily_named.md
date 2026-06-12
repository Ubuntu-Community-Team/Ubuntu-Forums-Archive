---
title: "zip all folders into separate, respectiveily named files."
date: 2009-02-04
forum: General Help
---

### Post by herot on 2009-02-04
I want to batch zip several folders into separate zip files with the same name as the folders. they all will have mp3's in them but i dont want to zip each song individually... How can i do this?

i found this code for doing mass files but it doesn't seem to work for folders...
```
for f in *; do zip "$f.zip" "$f"; done
```

---

### Post by Dies on 2009-02-04
```
for i in $( ls ); do $( zip -vr $i.zip $i ); done
```

---

### Post by herot on 2009-02-04
that seems like it might work however it has trouble with folder names with spaces in them.... it tries to do "Of Montreal" as "Of" and "Montreal" ...

how can i work around that?

```
 zip warning: name not matched: Alice

zip error: Nothing to do! (try: zip -vr Alice.zip . -i Alice)
        zip warning: name not matched: In

zip error: Nothing to do! (try: zip -vr In.zip . -i In)
        zip warning: name not matched: Chains

zip error: Nothing to do! (try: zip -vr Chains.zip . -i Chains)
        zip warning: name not matched: David

zip error: Nothing to do! (try: zip -vr David.zip . -i David)
        zip warning: name not matched: Bowie

zip error: Nothing to do! (try: zip -vr Bowie.zip . -i Bowie)
        zip warning: name not matched: Fleet

zip error: Nothing to do! (try: zip -vr Fleet.zip . -i Fleet)
        zip warning: name not matched: Foxes

zip error: Nothing to do! (try: zip -vr Foxes.zip . -i Foxes)
        zip warning: name not matched: Live

zip error: Nothing to do! (try: zip -vr Live.zip . -i Live)
        zip warning: name not matched: 1975

zip error: Nothing to do! (try: zip -vr 1975.zip . -i 1975)

zip error: Invalid command arguments (no such option: .)
        zip warning: name not matched: The

zip error: Nothing to do! (try: zip -vr The.zip . -i The)
        zip warning: name not matched: Rolling

zip error: Nothing to do! (try: zip -vr Rolling.zip . -i Rolling)
        zip warning: name not matched: Thunder

zip error: Nothing to do! (try: zip -vr Thunder.zip . -i Thunder)
        zip warning: name not matched: Revue

```

---

### Post by Dies on 2009-02-04
```

SAVEIFS=$IFS
IFS=$(echo -en "\n\b")
for i in $( ls ); do $( zip -vr $i.zip $i ); done
IFS=$SAVEIFS

```

That should work better. :)

---

### Post by herot on 2009-02-05
that worked! very helpful. thanks.:D

btw, could you explain what each part of that code does? just so ill know a little more.

---

### Post by herot on 2009-02-05
ALSO, how could i do this procedure but have it put the zip files in another directory/storage device?

---

### Post by herot on 2009-02-06
anyone?

---

### Post by vanadium on 2009-02-06
Much more simple, and will avoid issues with spaces:

> 
for i in * ; do zip -vr "$i.zip" "$i" ; done


How to put zips in another directory is left as an exercise to the reader.

---

### Post by herot on 2009-02-06
LOL nice! ok ill try to figure it out it cant be that hard. and thanks for the new code.

---

### Post by herot on 2009-02-06
OK this is how i did it

```
for i in * ; do zip -vr "$i.zip" "$i" ; mv "$i.zip" /move/zipfiles/here/ ; done
```

OR

```
for i in * ; do zip -vr "$i.zip" "$i" ; cp "$i.zip" /copy/zipfiles/here/ ; done
```

i couldn't figure out how to make the code just compress it directly to the other location so i just mv'd or cp'd them... but it works! :D

Thanks again everybody for your help!

---

