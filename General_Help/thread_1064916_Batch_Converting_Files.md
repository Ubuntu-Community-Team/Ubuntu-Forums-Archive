---
title: "Batch Converting Files"
date: 2009-02-09
forum: General Help
---

### Post by Starclopsofish on 2009-02-09
I made a thread asking for help similar to this one a while back for zipping multiple files from the cli, and I tried to adapt that for this purpose, but was unsucessful...

Basically I have a large library of flac music that I'd like to re-encode to ogg vorbis for my portable media player/phone. I kind of got this working with

for file in ./*; do ffmpeg -i "$file" -acodec vorbis -aq 100 "$file.ogg"; done

but the file extensions aren't named properly and for some reason media players have trouble playing these files even after they're re-named properly. Any help would be greatly appreciated!

---

### Post by geirha on 2009-02-09
Changing the extension can be done like this:
```

$ file="something.flac"
$ echo "$file" "${file/%.*/.ogg}"
something.flac something.ogg

```

Some portable media players only accept ogg vorbis audio within a certain bitrate. Try with something like
```
oggenc -o "${file/%.*/.ogg}" -q 6 "$file"
```

---

