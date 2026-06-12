---
title: "Simple convert RealAudio to MP3 script"
date: 2006-04-08
forum: Desktop Environments
---

### Post by adamkane on 2006-04-08
Totem can play RM files, but this is not yet the case with amaroK.

I don't think RealAudio has support for tags, and this is probably why RM support is not included in the audio-convert Nautilus-script.

Here is a simple script to convert an RM file to MP3, so that you can play RM files in amaroK. I don't know yet how to convert RM to OGG.

You need mplayer and lame installed to use the script.

```

mplayer filename.rm -ao pcm:file=filename.wav
lame --tt "TITLE" --ta "AUTHOR" --tl "ALBUM" --id3v2-only filename.wav filename.mp3

```

---

### Post by MenZa on 2006-04-09
You know, this ought to be stuck in "HOWTO"'s.. Good script :)

---

### Post by adamkane on 2006-04-09
My post isn't HOWTO worthy yet.

---

