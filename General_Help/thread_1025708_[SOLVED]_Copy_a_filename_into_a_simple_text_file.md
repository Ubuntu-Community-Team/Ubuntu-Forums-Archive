---
title: "[SOLVED] Copy a filename into a simple text file"
date: 2008-12-30
forum: General Help
---

### Post by perrti-y02 on 2008-12-30
Hello,
I am looking for a bash command that allows me to take a filename (/data/Music/Artist/Album/Song.mp3) and put it into a file to make a playlist (/data/playlists/Albumname.m3u)

Is there a command that does this?

I am not looking for a program that will create playlists for me. I am doing it mostly for fun.

---

### Post by Zorael on 2008-12-30
Like so?
```
$ echo /data/Music/Artist/Album/Song.mp3 >> /data/playlists/Albumname.m3u
```

---

### Post by Sukarn on 2008-12-30
or if you want to put the entire listing of the directory into the playlist then

```

$ ls /data/Music/Artist/Album > /data/playlists/Albumname.m3u

```

---

### Post by Zorael on 2008-12-30
Shouldn't that be '**ls -1**'?

---

### Post by Sukarn on 2008-12-31
> **Zorael said:**
> Shouldn't that be '**ls -1**'?

Doesn't make a difference. output in a file doesn't go in tabs

---

