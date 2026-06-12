---
title: "how to mass-rename files via the shell?"
date: 2009-05-08
forum: General Help
---

### Post by cyran on 2009-05-08
I'm looking to mass-rename a bunch of files and directories based on their existing filename. Specifically, I want to change their extension. I'm a complete newbie at using the shell, though. Any advice for guides?

---

### Post by spiderbatdad on 2009-05-08
[http://www.ubuntugeek.com/mrename-a-tool-for-easy-and-automatic-renaming-of-many-files.html](http://www.ubuntugeek.com/mrename-a-tool-for-easy-and-automatic-renaming-of-many-files.html)

---

### Post by cyran on 2009-05-08
Thanks! But this is on a kinda-broken system. Can't install any packages. (I...guess I should have mentioned that first. Somehow I forgot there's obviously some be *packages* for this...) Is there a way I can just wget the scripts or something?

---

### Post by spiderbatdad on 2009-05-08
well renaming is fairly easy via the shell just copying *.ext *.newext however this will not handle conversions. So if you cp ~/Pictures/*.jpg ~/Pictures.png the files would not be converted to png and would not open. So if you could be more specific...

---

### Post by ghostdog74 on 2009-05-08
if you have bash shell.
```

for files in *.ext
do
   mv "$files" ${files%.ext}.jpg
done

```
of if your broken system has Python. you can use the script in my sig called File renamer.eg
```

# python filerenamer.py -p ".ext" -e ".jpg" -l "*.ext"

```
remove -l to commit

---

