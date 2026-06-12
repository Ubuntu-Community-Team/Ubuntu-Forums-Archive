---
title: "Is there a program that can &quot;guess&quot; which charset a file name is?"
date: 2009-03-06
forum: General Help
---

### Post by tdn on 2009-03-06
I have some files with filenames in some strange encoding. 

Is there a program that can "guess" which encoding it is? I want to convmv them to utf8.

I thought that they were of charset Latin1, but they're not.

---

### Post by thtrgremlin on 2009-03-06
not exactly, because the charset just says how to display the individual characters. there is no interpretation of the data.

For filenames, I would just change them. Can't really 'convert' them. If it is a lot of files, you could use a script to have it remove characters specific characters, assuming there is a partial latin name.

that is as much as I know. How did you come across these files, if you don't mind me asking?

---

### Post by tdn on 2009-03-06
I think convmv is made exactly for converting a lot of file names to a different encoding. I use it all the time. I often get files with file names in from various charsets and I convert the file names with convmv.

Normally the filenames are latin1, so I will just do a iconvmv -f latin1 -t utf8 *
but this time the filenames are not latin1. I have tried a few different encodings, but this is not the correct source charset.

On how I came across these files, long and not very interesting story, but in short I just happen to have a few files from a lot of different parts of the world. And I guess some countries use wierd encodings.

---

### Post by thtrgremlin on 2009-03-06
likely country / language specific as they are meant to be. if it wee me, I would try to find what couny he files were from and install that charset. Sorry don't know how to help further

---

