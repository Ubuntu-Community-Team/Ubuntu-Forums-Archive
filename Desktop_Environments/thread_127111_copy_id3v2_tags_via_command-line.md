---
title: "copy id3v2 tags via command-line?"
date: 2006-02-08
forum: Desktop Environments
---

### Post by otey on 2006-02-08
I've just bought the sony ericsson w800 music phone. It supports mp3's but only from 192 kbps to some 64 kbps or something. 

All my mp3's are ripped in 320 kbps, so i found a way to convert files into 192..

```
lame -h -b 192 "$input_file" "$output_file"
```
I just need a way to copy the id3v2 info in the files, but how do i extract the id3v2 tags..

I tried this:

```
id3ren -copytagfrom="$input_file" -copyall "$output_file"
```
But it only copies the id3v1.1 or id3v1.0 info

---

