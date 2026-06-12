---
title: "Mass Change File Extensions"
date: 2009-01-03
forum: General Help
---

### Post by Uncle Che on 2009-01-03
I need some help getting a simple shell command needed to change file extensions from .JPG to .jpg. 

Here's the deal. When I pull the files off of my digital camera, they are saved as .JPG. I can upload them to facebook, photobucket and send them to relatives through email no problema. 

The problem is that my wife uses Friendster. She wants to upload them to Friendster. There's a hitch though. The programmers at Friendster are Windows centric. They have programmed their upload script to look for .jpg, .gif, etc. Now, it's not a problem for Windows because lower case and upper case file extensions are considered to be the same. Not so on Ubuntu Linux. In other words, my wife can't upload photos to facebook. 

I found these two little commands and tried to run them:

```
for file in *.JPG; do mv "$file" "{file%.JPG}.jpg"; done

for i in *.JPG; do base='basename "$i" .JPG'; mv "$i" "$base".jpg;done
```

The result for both of them was the same. Every file was deleted and one files was left named basename "$i" .JPG. jpg

Anyone have a better command to run?

Thanks

---

### Post by Sin@Sin-Sacrifice on 2009-01-03
Could this be what you're looking for? [http://www.franzone.com/2007/09/05/bash-script-to-change-file-extensions/](http://www.franzone.com/2007/09/05/bash-script-to-change-file-extensions/)

---

### Post by ghostdog74 on 2009-01-03
> **Uncle Che said:**
> 

```
for file in *.JPG; do mv "$file" "{file%.JPG}.jpg"; done

for i in *.JPG; do base='basename "$i" .JPG'; mv "$i" "$base".jpg;done
```



you do not need to use external commands like basename , therefore, just use the first version. A "$" is left out in "{file%.jpg}. It should be "${file%.JPG}.jpg".

---

