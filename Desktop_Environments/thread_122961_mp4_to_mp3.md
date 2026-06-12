---
title: "mp4 to mp3"
date: 2006-01-28
forum: Desktop Environments
---

### Post by Downtown on 2006-01-28
I know it's been covered before, but I'm getting mixed results.  I read the posts on [this]("http://ubuntuforums.org/showthread.php?p=630881#post630881") and [url="
http://ubuntuforums.org/showthread.php?p=589315#post589315"]this[/url] thread and I've tried both the scripts suggested.

If I try the first one, I conserve the ID3 tags, but the file is corrupted and the file is just static, and if I use the second one, I lose ID3 tags, but the file plays correctly.  I don't know much about scripts, so does anybody know how I can combine the two so that I can convert an m4a to mp3 while conserving my ID3 tags.

For quicker reference, these are the two scripts, in order of the links provided above...

```

#!/bin/bash
for i in *.m4a
do
base=`basename "$i" .m4a`
info=`faad -i "$i" 2>&1`
artist=`echo "$info" | grep artist: | sed s/artist:\ //g`
album=`echo "$info" | grep album: | sed s/album:\ //g`
song=`echo "$info" | grep title: | sed s/title:\ //g`
track=`echo "$info" | grep track: | sed s/track:\ //g`
year=`echo "$info" | grep date: | sed s/date:\ //g`
genre=`echo "$info" | grep genre: | sed s/genre:\ //g`
faad -w "$i"| lame -h -b 128 - "$base.mp3"
#id3 -a "$artist" -A "$album" -t "$song" -T "$track" -y "$year" -g "$genre" "$base.mp3"
id3v2 -a "$artist" -A "$album" -t "$song" -T "$track" -y "$year" -g "$genre" "$base.mp3"
done

```

```

#!/bin/bash
for i in *.m4a
do
	NO_SPACE=`echo $i | sed -e "s/ /_/g"`
	mv "$i" "$NO_SPACE"
done

for i in *.m4a
do
	faad $i
	lame *.wav
	rm *.wav
	rm "$i"
done

for i in *.mp3
do
	NO_WAV=`echo $i | sed -e 's/.wav//g' -e 's/_/ /g'`
	mv "$i" "$NO_WAV"
done

```

---

### Post by Downtown on 2006-01-28
bump

---

