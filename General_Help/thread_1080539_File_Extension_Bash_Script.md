---
title: "File Extension Bash Script"
date: 2009-02-25
forum: General Help
---

### Post by linux4me on 2009-02-25
I have a bash script that I use to rename JPEG images in batches. One part of the script changes the extension from all caps to lower case:
```
for fname in $path*.JPG; do
   rename 's/\.JPG$/\.jpg/' $fname
done
```
The script works fine if there *is* a file with an extension that is all caps, but if there isn't, I get the following output:
> Can't rename /home/username/Desktop/*.JPG /home/username/Desktop/*.jpg: No such file or directory
I would like to add a conditional statement or something to prevent this part of the script from executing if there are no files that have an uppercase extension (*.JPG). I thought the for loop I have would do that, but evidently it doesn't.

What's the best way to prevent the rename command from executing if there are no files with uppercase extensions?

---

### Post by TCSnyder on 2009-02-25
Try putting "*.JPG" in quotes.

---

### Post by opscure on 2009-02-25
```
for fname in $path*.JPG; do if [ -e *.JPG ]; then rename 's/\.JPG$/\.jpg/' $fname; fi; done
```

---

### Post by heindsight on 2009-02-25
> **opscure said:**
> ```
for fname in $path*.JPG; do if [ -e *.JPG ]; then rename 's/\.JPG$/\.jpg/' $fname; fi; done
```

if there's more than one .JPG file, that will cause an error like:
```
bash: [: too many arguments
```

you can specify multiple files to rename anyway, so i don't really see the need for putting this in a for loop, you could just do:
```
rename 's/\.JPG/\.jpg/' $path*.JPG
```

this will give an error if $path*.JPG doesn't match any existing files, to avoid that, you could do something like:

```

FILES=$(echo $path*.JPG)
if [ "${FILES%\*.JPG}" != "$path" ]; then
    rename 's/\.JPG/\.jpg/' $FILES
fi

```

---

### Post by opscure on 2009-02-25
> **heindsight said:**
> if there's more than one .JPG file, that will cause an error like:
```
bash: [: too many arguments
```


Indeed it would... I don't know what I was thinking.  Thanks for the catch.

---

### Post by linux4me on 2009-02-25
> **heindsight said:**
> 
```

FILES=$(echo $path*.JPG)
if [ "${FILES%\*.JPG}" != "$path" ]; then
    rename 's/\.JPG/\.jpg/' $FILES
fi

```

Thanks, Heindsight, that worked perfectly.

---

