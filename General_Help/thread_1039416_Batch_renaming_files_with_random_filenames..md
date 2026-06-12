---
title: "Batch renaming files with random filenames."
date: 2009-01-14
forum: General Help
---

### Post by murphykieran on 2009-01-14
I have a folder with hundreds of photographs that I wish to rename all with random filenames like strings of random digits or letters.  They are currently called things like john01.jpg john02.jpg christmas 2008 001.jpg christmas 2008 002.jpg etc.

Someone on another forum suggested the following command to use:

```
for f in *.jpg; do mv $f $RANDOM.jpg; done
```

But when I do that, it gives an error message for each of the files it tries to move.

```
mv: target `13000.jpg' is not a directory
mv: target `17594.jpg' is not a directory
mv: target `2689.jpg' is not a directory
etc. etc.
```These appear to be the new filenames it's trying to give them.  It will only rename a single file and give errors for the rest.

The weird thing is, I tried it on a few folders of files I actually wanted to rename and it gives the same error, but if I go to home/pictures which contains subfolders of all my photos and which itself contains a handful of random jpegs, it works!  It took the dozen or so photos in that folder and renamed them with files like 235423.jpg 219987.jpg 82639.jpg etc.

And clue as to what's going on?

---

### Post by murphykieran on 2009-01-14
Okay, some quick experiment shows that it will only work on files that don't have any spaces in their filenames.  I tried it on a few random folders and it only renamed the files that had no spaces in the filename.

Does anyone know how to modify the following command so it will work with file that include spaces in the filename?  I tried removing the .jpg from *.jpg (some are .jpeg and they're all JPEGs so there's no need for it anyway) but it's making no difference.

```
for f in *.jpg; do mv $f $RANDOM.jpg; done
```

While I'm at it, is there an explanation somewhere for what the different colors mean when doing an ls command in the terminal?  I was looking at a folder of photos and files ending in .jpg were coloured purple, but files ending in .JPG were coloured black.  What does mean?

---

### Post by qazatqazah on 2011-01-11
A pair of double quotes will do the trick: it will prevent the file name from breaking. 
Here I also added handling the extensions jpeg and JPG:

```
for f in *.jpg *.jpeg *.JPG; do mv "$f" $RANDOM.jpg; done
```

---

### Post by emergingtechnologies on 2011-06-14
Just used this and it worked beautifully!  I love it when I search for something and the answer is already here!

---

### Post by alphacrucis2 on 2011-06-14
I guess there is some small chance that $RANDOM generates a duplicate number causing the rename to the second instance to fail. I presume this would be rare though.

---

