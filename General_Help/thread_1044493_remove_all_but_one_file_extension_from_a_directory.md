---
title: "remove all but one file extension from a directory"
date: 2009-01-19
forum: General Help
---

### Post by tigershark88 on 2009-01-19
i am copying my music collection over from my windows xp machine. i would like to do some clean up at this time. in many of the folders in the music directory there are files such as .ini, .jpg, .db. I would like to remove all of these so i just have the .mp3 files. i know the .jpg are album art but i would like to get rid of those as well so i just have the music files. 
My files are automatically organized by itunes on the windows pc so there are many folders. Is it possible to remove all files with a file extension other than .mp3 from each folder with one command in ubuntu? doing it to each artists folder would be too time consuming.

---

### Post by heindsight on 2009-01-19
You can use
```
find /path/to/music/directory -type f -not -iname "*.mp3" -exec rm \{\} \;
```

Make sure you get the path right. If you want to make sure you're deleting the right files, you could first do:
```
find /path/to/music/directory -type f -not -iname "*.mp3"
```
(it will give you a list of the files that will be deleted)

---

### Post by dcstar on 2009-01-20
> **tigershark88 said:**
> i am copying my music collection over from my windows xp machine. i would like to do some clean up at this time. in many of the folders in the music directory there are files such as .ini, .jpg, .db. I would like to remove all of these so i just have the .mp3 files. i know the .jpg are album art but i would like to get rid of those as well so i just have the music files. 
My files are automatically organized by itunes on the windows pc so there are many folders. Is it possible to remove all files with a file extension other than .mp3 from each folder with one command in ubuntu? doing it to each artists folder would be too time consuming.

Try (but test first):

```
rm *[!mp3$]
```

The recursive option may work, but that would have to be tested.

---

### Post by heindsight on 2009-01-20
> **dcstar said:**
> Try (but test first):

```
rm [!.mpg]*
```

I don't see how that would work. It would delete all files in the current directory with names not starting with one of the characters . m p g

---

### Post by dcstar on 2009-01-20
> **heindsight said:**
> I don't see how that would work. It would delete all files in the current directory with names not starting with one of the characters . m p g

Hmmm, let me look at this again.

Yep, I thought a regexp that worked with the start of a string would work with the whole string, but it doesn't - very inconvenient.

Ok, try this:

```
rm *[!mp3$]
```

When using "ls" that command will only list files **not** ending in mpg, so rm will work (it just did on my test).

---

### Post by tigershark88 on 2009-01-20
heindsight that first post did it! you are brilliant. thank you for your help!

---

### Post by heindsight on 2009-01-21
> **dcstar said:**
> 
Ok, try this:

```
rm *[!mp3$]
```

When using "ls" that command will only list files **not** ending in mpg, so rm will work (it just did on my test).

No.

Have a look at the pathname expansion section of the bash manual.
[...] matches exactly one character so 
```
rm *[!mp3$]
```
will remove all files not ending in one of the characters m p 3 or $
The other problem with using just rm here, is that it won't delete files from any subdirectories, only files in the current dir.

---

