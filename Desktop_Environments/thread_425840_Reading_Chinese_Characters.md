---
title: "Reading Chinese Characters?"
date: 2007-04-27
forum: Desktop Environments
---

### Post by kolslorr on 2007-04-27
Hello,

I do not know where to ask this, so i post here instead.

I have some mp3 files with Chinese filenames, and I am able to read them properly in Nautilus file browser. 

However, for certain application like Armarok, those file names cant be interpreted. I know it has something to do with the unicode thing, but how do I solve this problem with problematic applications that doesnt read unicodes?

Another example is Rythmbox, it reads some files ok, but some not. duno why. 

PLease help~~~

---

### Post by gabng on 2007-04-28
Hi, you're right in that it has to do with UTF-8 encoding.

Nautilus reads file names whereas music apps read tag data, if they don't support the specific encodings of your mp3 tags, then you'll see weird characters.  So it's recommended that you convert them to UTF-8 encoding.

If you have Windows installed, you can use a program called Mp3Tag.  It supports mass conversion to ID3v2.4 ( UTF-8 ).  It's worked wonders for me converting few thousand Chinese mp3s very quickly.  And the tags can be read under both Windows and Linux apps.

If you only have Linux installed, use EasyTag.  It supports mass conversion to ID3v2.3 tags.

The music players themselves also matter.  I haven't tried Amorak, but I tried Rythmbox, Exaile, Songbird and Audacious.  Exaile couldn't read anything at all, before or after conversion.  Rythmbox reads them pretty well after conversion, with less than 10 exceptions among few thousand.  Audacious reads all the converted files correctly I think (haven't verified).  And Songbird reads everything after conversion fine (I converted to ID3v2.4, so I installed the "Taglib metadata handler" addon to read the ID3v2.4 tags).

Hope this'll solve your problem.  Cheers.

---

### Post by kolslorr on 2007-04-29
Wow, thats a very comprehensive explanation. Thanks for your reply!

I am installing Easytag right now to try it out, hopefulyl it works!!

---

