---
title: "how can i extract .exe files?"
date: 2009-06-21
forum: General Help
---

### Post by flyingsliverfin on 2009-06-21
i know that .exe's are extractable because when i right click one on ubuntu there is an "extract here"option. however,when i click it it gives me this outptut:

[/home/ubuntu/Desktop/U904p.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/ubuntu/Desktop/U904p.exe or
          /home/ubuntu/Desktop/U904p.exe.zip, and cannot find /home/ubuntu/Desktop/U904p.exe.ZIP, period.

i want to extract it because i think i can extract it, then modify the executable for my needs... i didn't like the way it modified my memory stick :sad:

---

### Post by HavocXphere on 2009-06-21
An exe files is not extractable by nature.

However, some exe files are "packed" and you can unpack them. (Google exe compressors. An example would be UPX)

> extract it, then modify the executable for my needs
You can modify executables. It usually does not involve "extracting" though. You would reverse engineer it to a certain extent. Going that route is *very* technical & time-consuming.

It involves a lot of this stuff: [[link]]("http://img296.imageshack.us/img296/5838/picture5xk1.jpg") Thats ASM ie assembly language.

Judging by your post, I'd say that you are not quite ready for that degree of technical obstacles.

---

### Post by rsmseys on 2009-06-21
Some exe's are compiled, where as others are an auto extracting zip file. So basically, if it extracts then it's a simply zip file with a program overlay (made with winRar or another packer) and if it doesn't extract, then it's a simple compiled application, in which case, you CAN'T extract it.

---

### Post by dcraven on 2009-06-21
I'm not sure I'm going to be much help here, but generally exe files are not extractable.

Some may be simply archive files renamed for Windows use however. I'd probably start with the "file" command to see what type of file it is, then go from there if possible.

So, in a terminal, fun "file $YOURFILE" and see what the output is.

Cheers,
~djc

---

### Post by flyingsliverfin on 2009-06-21
i got it using p7xip :) it worked

---

### Post by 3Miro on 2009-06-21
rar can make .exe files that are self extracting archives, one can either extract it using rar or run it if he has no rar. That is under windows.

Under Linux, you try using wine, sometimes it works for me.

---

### Post by flyingsliverfin on 2009-06-22
ok, but as i said i managed to extract it in ubuntu using p7zip. otherwise i could have tried wine i guess...

---

### Post by Steelmourne on 2009-06-22
You could also try universal extractor under WINE. Can extract from exe's.

---

### Post by flyingsliverfin on 2009-06-22
yea, thx everyone, no offence but i already got it :P

---

### Post by fcvsub on 2009-07-31
all what you need , is re-name the first  file to be ending with .rar , have fun :)

---

