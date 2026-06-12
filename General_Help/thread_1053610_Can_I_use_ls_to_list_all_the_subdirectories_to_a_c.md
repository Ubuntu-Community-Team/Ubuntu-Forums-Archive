---
title: "Can I use ls to list all the subdirectories to a certain depth?"
date: 2009-01-28
forum: General Help
---

### Post by Yes on 2009-01-28
I've got my Music stored in the format Music/Artist/Album/songs.  I'd like to get a listing of all my albums, so I figured the easiest way would be to somehow use ls to list all the subdirectories in Music, but not the songs.  So can I get ls -R to only list subdirectories three directories deep, and then quit?  Or is that not possible?

Thanks!

---

### Post by sisco311 on 2009-01-28
I'm not sure if I understand your question correctly, but I think you can use the find command:
```
find path/to/music -type d -maxdepth 3
```
```
man find
```

Can you post an example?

---

### Post by cdtech on 2009-01-28
To list only the directories just do a:
```
$ ls -d Music/Artist/Album/*/
```
Or however deep you want it to go......
> I'd like to get a listing of all my albums
```
$ ls -d Music/Artist/*/
```

---

### Post by Yes on 2009-01-28
Alright - I store my songs in a folder for the album, which is inside the folder for the artist, which is inside the Music folder.  E.g., the path to Flood.ogg would be '~/Music/Tool/Undertow/Flood.ogg'.  I want to get a listing of all the albums, so I guess I just want to list all the subdirectories in ~/Music except the first "level"... is there any way to do this, or am I just being picky and lazy?

---

### Post by cdtech on 2009-01-28
Did you try the suggestion above? :
```
$ ls -d Music/*/
```
What do you mean except the first level? Isn't your Music folder the first level?

---

### Post by Yes on 2009-01-28
Ooh, thanks that worked.  It'd be great if I just got a list of the albums, e.g. Undertow instead of Music/Tool/Undertow, but if thats not possible this is fine.

---

### Post by sisco311 on 2009-01-28
You can use awk:
```
ls **blablabla** | awk -F '/' '{ print $3 }'
```

---

### Post by Yes on 2009-01-28
Excellent!  Thanks so much, both of you :)

---

