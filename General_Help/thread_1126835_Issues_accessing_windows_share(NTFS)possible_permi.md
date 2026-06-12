---
title: "Issues accessing windows share(NTFS)/possible permissions issue"
date: 2009-04-15
forum: General Help
---

### Post by Disorder on 2009-04-15
Hello I'm using kubunu 8.11 and have file server running Vista Ultimate

I went into dolphin > network > and then added a network folder

Typed in my winodws un/pw and was able to browse to my shared windows drive(NTFS) and view all of it's contents

I browse to my music folder and add songs to Amarok but when I play them I get:

No suitable input plugin. This often means that the url's protocol is not supported. Network failures are other possible causes.
smb://username@10.0.0.x/E/Music/12 Hour Turn/Bend Break Spill/01-I To Had Potential .mp3

---

### Post by cariboo on 2009-04-16
The problem is that there are spaces in the directory and file names. You will have tp delimit the names using \, eg:

```
mb://username@10.0.0.x/E/Music/12\Hour\Turn\Bend\Break\Spill\01-I\To\Had\Potential\.mp3 
```

Linux sees each space as the start of a new file name.

Jim

---

### Post by Disorder on 2009-04-16
There is no way around it? There is no way I could reorganize my music collection in such a way as it would not make sense.

---

