---
title: "need help with little rm script"
date: 2009-04-10
forum: General Help
---

### Post by SlugSlug on 2009-04-10
I have /photos which contains /indoor and /ouutdoor sub directorys and in each of them are sub directory's of albums.  now what i want to do is search for 01.jpg and remove its parent dir, thus leaving me only with folders that contain proper file names. :guitar:

how do you do that?

---

### Post by kpatz on 2009-04-10
Can you please clarify?  I don't understand what you're trying to do.

So, you have photos/indoor/album1 and photos/outdoor/album1 (and album2, etc.)...

And you have a file named 01.jpg...

You want to find 01.jpg... but then what?  Say you find it in photos/outdoor/album10... you want to move it up a level (say to photos/outdoor)?

If you're in the directory already (photos/outdoor/album10), the command **mv 01.jpg ..** will move 01.jpg to the parent directory (in this case outdoor).

---

### Post by SlugSlug on 2009-04-10
what i have is like 
/photos/indoor/album1/01.jpg 02.jpg
and some like 
/photos/indoor/album2/bob.jpg jimmy.jpg

what i want to do is remove all the albums that dont have track names

---

### Post by kpatz on 2009-04-10
> **SlugSlug said:**
> what i have is like 
/photos/indoor/album1/01.jpg 02.jpg
and some like 
/photos/indoor/album2/bob.jpg jimmy.jpg

what i want to do is remove all the albums that dont have track namesSo, you have...

/photos/indoor/album1/(bunch of jpg files)
/photos/indoor/album2/(bunch of jpg files)
/photos/indoor/album3/(empty directory, no files here)
/photos/indoor/album4/(bunch of jpg files)

and you want to delete the empty directories (album3 above)?

Run this first:
```

find /photos -type d -empty

```

and verify that it gives just the empty directories, then, to remove them:

```

find /photos -type d -empty | xargs rmdir

```

---

### Post by SlugSlug on 2009-04-10
no i have 
#
/photos/indoor/album1/(bunch of jpg files called 01.jpg 02.jpg etc)
/photos/indoor/album2/(bunch of jpg files 01.jpg 02.jpg )
/photos/indoor/album3/(empty directory, no files here)
/photos/indoor/album4/(bunch of jpg files called bob.jpg jimmy,jpg etc )

what i want to do is remove album 1 2 3 but lleave 4 as its named properly

---

### Post by kpatz on 2009-04-10
So, you basically want to delete all albums that only have jpg file names that are numbers?

You could do it this way:

```

# delete jpg files that have only digits in the name (e.g. 01.jpg)
find /photos -regex '.*/[0-9]+\.jpg' -rm {} \;
# now delete empty albums/folders
find /photos -type d -empty | xargs rmdir

```

The drawback is if a folder has both number and non-number jpgs in them, the number ones will be deleted but the non-number ones will remain, as will the album.

Play it safe and back up the /photos directory before running anything...

---

### Post by SlugSlug on 2009-04-10
Thank you very much for your help I dont think that will work due to there being non number files in the dir aswel IE cover.bmp ect - i was also hopeing to do the same with files simlaure to the name 'image01.jpg'

---

