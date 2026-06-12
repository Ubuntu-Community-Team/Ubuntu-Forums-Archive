---
title: "Managing files (two or more paths to 1 file? Auto updating links to a changed file?)"
date: 2009-06-23
forum: General Help
---

### Post by Glace on 2009-06-23
//Sorry if this is in the wrong section, I'm a little confused/noobish so bear with me. Please tell me if my query is unclear.

I would like to create links that will still work once a file is moved or renamed.

I know the "Bookmarks" in Nautilis are like this, (you set a bookmark, rename the file, the bookmark changes) but I would like to give these links a location in the filesystem too.



An example of why I want this: I have a folder with all my films, but I want to categorize all films into folders of films I've watched and ones I haven't, I also want to categorize all films into 2 folders 'bad' and 'good', I also want to categorize all films into folders of if my friend has seen it, etc. etc. etc.

My solution was to make a folder with all files, then links to those files, then breaking up the links into the folders (categories) I require. giving me 2 or more ways to get to the same file.

Which comes back to my original question, because my solution is unmanageable if all the links get stuffed once I mess with the files.

So is there a better way of doing this? A file manager which can make 2 or more paths to a file?
I'm happy to go CLI if you guys know a way I can solve this.

---

### Post by Bachstelze on 2009-06-23
What you want is called "hard links". Here's an example:

I create a directory, and inside it, I create four files named [font="monospace"]file1[/font], [font="monospace"]file2[/font], [font="monospace"]file3[/font] and [font="monospace"]file4[/font]:

```
firas@iori test % mkdir allfiles
firas@iori test % cd allfiles
firas@iori allfiles % touch file1 file2 file3 file4
firas@iori allfiles % ls -l
total 0
-rw-r--r-- 1 firas firas 0 2009-06-23 14:05 file1
-rw-r--r-- 1 firas firas 0 2009-06-23 14:05 file2
-rw-r--r-- 1 firas firas 0 2009-06-23 14:05 file3
-rw-r--r-- 1 firas firas 0 2009-06-23 14:05 file4

```

Now I create two other dirs called [font="monospace"]odd[/font] and [font="monospace"]even[/font], in whichI'm going to put links to all odd- and even-numbered files, respexctively:

```
firas@iori allfiles % cd ..
firas@iori test % mkdir odd even
firas@iori test % ls -lR
.:
total 12
drwxr-xr-x 2 firas firas 4096 2009-06-23 14:05 allfiles
drwxr-xr-x 2 firas firas 4096 2009-06-23 14:09 even
drwxr-xr-x 2 firas firas 4096 2009-06-23 14:09 odd

./allfiles:
total 0
-rw-r--r-- 1 firas firas 0 2009-06-23 14:05 file1
-rw-r--r-- 1 firas firas 0 2009-06-23 14:05 file2
-rw-r--r-- 1 firas firas 0 2009-06-23 14:05 file3
-rw-r--r-- 1 firas firas 0 2009-06-23 14:05 file4

./even:
total 0

./odd:
total 0

```

Now I'm going to create the links, this is done with the [font="monospace"]ln[/font] command.

```
firas@iori test % cd odd
firas@iori odd % ln ../allfiles/file1
firas@iori odd % ln ../allfiles/file3
firas@iori odd % cd ../even
firas@iori even % ln ../allfiles/file2
firas@iori even % ln ../allfiles/file4
firas@iori even % cd ..
firas@iori test % ls -lR
.:
total 12
drwxr-xr-x 2 firas firas 4096 2009-06-23 14:05 allfiles
drwxr-xr-x 2 firas firas 4096 2009-06-23 14:08 even
drwxr-xr-x 2 firas firas 4096 2009-06-23 14:08 odd

./allfiles:
total 0
-rw-r--r-- 2 firas firas 0 2009-06-23 14:05 file1
-rw-r--r-- 2 firas firas 0 2009-06-23 14:05 file2
-rw-r--r-- 2 firas firas 0 2009-06-23 14:05 file3
-rw-r--r-- 2 firas firas 0 2009-06-23 14:05 file4

./even:
total 0
-rw-r--r-- 2 firas firas 0 2009-06-23 14:05 file2
-rw-r--r-- 2 firas firas 0 2009-06-23 14:05 file4

./odd:
total 0
-rw-r--r-- 2 firas firas 0 2009-06-23 14:05 file1
-rw-r--r-- 2 firas firas 0 2009-06-23 14:05 file3

```

Now you can see that each file is accessible at two locations. To verify that the two locations indeed point to the same file, let's write to one and verify that the changes applied to the other as well:

```

firas@iori test % echo "This is the file number 1" | tee allfiles/file1
This is the file number 1
firas@iori test % cat allfiles/file1
This is the file number 1
firas@iori test % cat odd/file1
This is the file number 1

```

Good. Now let's try to move a file and see if we don't get a "broken link":

```
firas@iori test % mkdir otherdir
firas@iori test % mv allfiles/file1 otherdir
firas@iori test % cat otherdir/file1
This is the file number 1
firas@iori test % cat odd/file1
This is the file number 1

```

I think this is what you want. :)

---

### Post by Glace on 2009-06-23
wow... Thanks yes that's exactly what I want :D

The links even show up like normal files in nautilis and you can edit them to change to original file!

Though I think I'll brush up on my knowlege on managing files in terminal and just use it instead of a file manager.

Thanks very much :D

One more thing, how do I set the thread to solved, can't find it in 'Thread tools'. ;)

---

### Post by lloyd_b on 2009-06-23
> **Glace said:**
> wow... Thanks yes that's exactly what I want :D

The links even show up like normal files in nautilis and you can edit them to change to original file!

Though I think I'll brush up on my knowlege on managing files in terminal and just use it instead of a file manager.

Thanks very much :D

One more thing, how do I set the thread to solved, can't find it in 'Thread tools'. ;)

One thing to be aware of - hard links *must* be to files on the same filesystem, unlike symlinks which can point to a file anywhere (even one that doesn't exist).  This may or may not be a problem for you...

Lloyd B.

---

### Post by Glace on 2009-06-23
Okay thanks for the warning. :)

---

### Post by Bachstelze on 2009-06-23
> **lloyd_b said:**
> One thing to be aware of - hard links *must* be to files on the same filesystem, unlike symlinks which can point to a file anywhere

The drawback being that if you move the original file away, the symlink will be broken.

---

### Post by Glace on 2009-06-23
Yeah I gathered that.

Hard linking to a directory, can it be done?

---

### Post by Bachstelze on 2009-06-23
> **Glace said:**
> Hard linking to a directory, can it be done?

Why not try and find out? ;)

---

### Post by Glace on 2009-06-23
Failed when I tried,
in the help for 'ln' it says: 

```
-d, -F, --directory allow the superuser to attempt to hard link
                                directories (note: will probably fail due to
                                system restrictions, even for the superuser)
```

---

### Post by Bachstelze on 2009-06-23
Indeed, you can't normally create hard links on directories. You can try to force it, but as the man says, it will probably fail anyway.

---

