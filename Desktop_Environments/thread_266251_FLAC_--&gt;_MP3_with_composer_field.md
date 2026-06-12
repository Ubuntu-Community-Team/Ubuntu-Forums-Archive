---
title: "FLAC --&gt; MP3 *with* composer field"
date: 2006-09-27
forum: Desktop Environments
---

### Post by musicinmybrain on 2006-09-27
I wish to batch convert a single directory or a directory tree full of FLACs to MP3s. The catch is that I must preserve all the metadata... including the composer field.

Lame does NOT support any tags not available in id3v1. Some standalone command-line taggers do, but don't support the composer tag.

I'm looking for either (a) a GUI tool or script that can do batch conversions and preserves the composer field or (b) a command-line MP3 tagger capable of writing the composer field. (I can write my own shell script to handle the batch conversion part and just call the tagger.)

The only software I've found that can write the composer tag in MP3s is EasyTag, and, while that's a great piece of software, it's not useful for helping with batch conversions.

I realize none of this would be a problem if I were converting to Ogg Vorbis, but I need to convert to MP3.

Does anyone know of a program that will do what I seek? Please make sure you realize I need to write the composer tag. Thanks for your suggestions!

---

### Post by musicinmybrain on 2006-09-27
Well, it turns out I can use foobar2000 under wine to do this and it works perfectly. Sadly, I can't find a "pure Linux" solution.

---

