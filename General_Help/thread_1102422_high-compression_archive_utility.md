---
title: "high-compression archive utility"
date: 2009-03-21
forum: General Help
---

### Post by rhcm123 on 2009-03-21
I have killed the old days of backing up photos to DVD's (un economic, and unenviromentaly freindly. Also, unwallet freiendly) and have backed them all up to the File Server. However, that thing is kinda running low on capacity - and i want to free up some space.

I rarely, if at all access the photos that are archived on the file server. therfore, i wanna dump them into an archive that compresses them to a very small size (i heard there are ones that can cut size by 50%!!) and are realtively easy to use. Because these photos are organized by directories, i need an archive that also supports directories.

Any ideas?

---

### Post by snova on 2009-03-21
[7-zip]("http://en.wikipedia.org/wiki/7-zip").

If you have a GUI on this server, installing the **p7zip-full** package is enough for File Roller to be able to support the format.

If you only have the command line available:

```
7z --help
```

---

### Post by Slim Odds on 2009-03-21
> **rhcm123 said:**
> 
I rarely, if at all access the photos that are archived on the file server. therfore, i wanna dump them into an archive that compresses them to a very small size (i heard there are ones that can cut size by 50%!!) and are realtively easy to use. Because these photos are organized by directories, i need an archive that also supports directories.

Depending on the file format, the compression will probably not be that much. Unless you have a lot of BMP files. JPG is pretty highly compressed already. PNG is typically pretty compressed as well.

---

### Post by InfectedWithDrew on 2009-03-21
I heard PeaZip runs on Linux as well.  And it's supposedly better than 7-zip, though I've never used it.

----------------
Now playing: [Switchfoot - Underwater](http://www.foxytunes.com/artist/switchfoot/track/underwater)

---

### Post by lisati on 2009-03-21
As already noted by others, many image file formats are already compressed, so you might not be ale to achieve much in the way of savings (if anything)

If the drive is NTFS and accessible from a Windows machine you might want to check out the Windows "compress data to save space" option. Be warned, however, that it can take a while if you have a lot of files.

EDIT: BTW, I'm **not** thinking of the "send to->compressed file" option.

---

### Post by Slim Odds on 2009-03-21
> **lisati said:**
> If the drive is NTFS and accessible from a Windows machine you might want to check out the Windows "compress data to save space" option. Be warned, however, that it can take a while if you have a lot of files.

But, as mentioned, since most graphic files are all ready highly compressed, the "disk compress" will not help much.

Best bet is a bigger drive.

---

### Post by lovinglinux on 2009-03-21
I guess you don't need another utility, since the default archive manager is capable of compressing files using several algorithms, including lzma, which is used by 7-zip. 

Nevertheless, I think you probably not be satisfied with the results, since images are usually already compressed by their own formats, unless you are talking about lossless formats like TIFF.

---

### Post by lisati on 2009-03-21
> **Slim Odds said:**
> But, as mentioned, since most graphic files are all ready highly compressed, the "disk compress" will not help much.

Best bet is a bigger drive.

Well spotted. I'm not sure how the Windows manages its compressions: the one on the "send to" menu seems to make a regular ".zip" archive, but I have no idea of the technical details of what happens if you select a file within Windows, click properties, and select the "compress file" checkbox. My guess is that it somehow tries to use the "free" space at the end of partly used sectors. (This is just a guess)

I might have to look at that option (a larger capacity disk) for my video files some time soon as well. By the time you have the original footage (along with relavent stills), an edited version, project files (in case you need to come back and edit it again), music files and disk images..... it can take up a lot of space.

---

### Post by Yashiro on 2009-03-21
Most useful, .gz
Higher compression but slow, .bz2
Most compression but very slow, .lzma
Cross platform ease of use, .zip

If it's images you want to compress there are various tools that can strip jpeg headers or recompress png's.

---

### Post by sekinto on 2009-03-21
I've had the best results with lzma and bzip2 compression. Both can be done with Ubuntu's archiving utility (File Roller).

---

### Post by Slim Odds on 2009-03-21
> **Yashiro said:**
> Most useful, .gz
Higher compression but slow, .bz2
Most compression but very slow, .lzma
Cross platform ease of use, .zip

Correction, most compression "rm"   ;)

---

### Post by lisati on 2009-03-21
> **Slim Odds said:**
> Correction, most compression "rm"   ;)

Used well, that would win. But isn't that method a bit lossy?

---

### Post by Slim Odds on 2009-03-21
> **lisati said:**
> Used well, that would win. But isn't that method a bit lossy?

Oh, I see, you want "bidirectional compression" LOL

Yes, it is **quite** lossy.....

---

### Post by rhcm123 on 2009-03-21
Which is the highest compression, .7z, .lzma, or .bz2?

---

### Post by Slim Odds on 2009-03-22
> **rhcm123 said:**
> Which is the highest compression, .7z, .lzma, or .bz2?

Probably depends on the file. You'll have to do some experimentation. These all have different options for compression level also (more compression==more time).

---

### Post by rhcm123 on 2009-03-22
> **Slim Odds said:**
> Probably depends on the file. You'll have to do some experimentation. These all have different options for compression level also (more compression==more time).

ok, i'll go see. i'm compressing mostly .jpeg and .rar files, if this helps

---

### Post by mb_webguy on 2009-03-22
An rar is already a compressed archive.  You won't really get any benefit from further compression.  It's like adding a zip file to a zip file.

And as others have said, jpg files are also already compressed, so it's doubtful you'll get much extra compression from them either.

In my experience, 7z provides very high compression rates.  I would say it's the best, but I don't have numbers to back up that claim, and it would almost certainly vary depending on the type and number of files being compressed.

To get the maximum compression using 7z, use the following command in the terminal (since File Roller doesn't give you the option to set the compression level).```
7z a -t7z -m0=lzma -mx=9 -mfb=64 -md=32m -ms=on *archive_name* *file_list*
```I have this aliased as "7zultra" so I can just type "7zultra *archive_name* ./*" to archive all files in the current directory.  The difference between this and the default settings is slight, but noticeable when creating very large archives.

---

### Post by snova on 2009-03-22
> **rhcm123 said:**
> Which is the highest compression, .7z, .lzma, or .bz2?

7zip is an archive format, however it accomodates for many different compression formats. LZMA is the default, and is somewhat better than Bzip2.

A few small comparisons: [http://celtickane.com/articles/compressionComparison.php](http://celtickane.com/articles/compressionComparison.php)

---

### Post by rhcm123 on 2009-03-22
> **mb_webguy said:**
> 
To get the maximum compression using 7z, use the following command in the terminal (since File Roller doesn't give you the option to set the compression level).```
7z a -t7z -m0=lzma -mx=9 -mfb=64 -md=32m -ms=on *archive_name* *file_list*
```I have this aliased as "7zultra" so I can just type "7zultra *archive_name* ./*" to archive all files in the current directory.  The difference between this and the default settings is slight, but noticeable when creating very large archives.

Thank you! This command cut off about 50~ megs of space from the other archive (which cut the basic size by about 25%. Just another quick question - how did you create the launcher? Not with, ln, right?

---

### Post by MaxIBoy on 2009-03-22
Edit the file ~/.bashrc to add an alias. Aliases are formatted like this:
```
alias "shortcut command"="really long and tedious-to-type command"
```
Note that you only need quotes if a command contains whitespace.


Then run the command "source ~/.bashrc" to reload your settings and apply the alias.

In this example, the alias would be:
```
alias 7zultra="7z a -t7z -m0=lzma -mx=9 -mfb=64 -md=32m -ms=on"
```

---

### Post by rhcm123 on 2009-03-22
> **MaxIBoy said:**
> Edit the file ~/.bashrc to add an alias. Aliases are formatted like this:
```
alias "shortcut command"="really long and tedious-to-type command"
```
Note that you only need quotes if a command contains whitespace.


Then run the command "source ~/.bashrc" to reload your settings and apply the alias.

In this example, the alias would be:
```
alias 7zultra="7z a -t7z -m0=lzma -mx=9 -mfb=64 -md=32m -ms=on"
```

thank you... the only problem is that this takes like 3 hours **per file**... the good thing is that i don't plan on opening up this archive for a very long time

---

### Post by Slim Odds on 2009-03-23
> **rhcm123 said:**
> thank you... the only problem is that this takes like 3 hours **per file**... the good thing is that i don't plan on opening up this archive for a very long time

Compression takes a **LOT** longer than decompression. The hard work in on the compression side (lots of analysis).

---

### Post by rhcm123 on 2009-03-23
> **Slim Odds said:**
> Compression takes a **LOT** longer than decompression. The hard work in on the compression side (lots of analysis).

i think that means it will take 2 years to do all of this... hmmm... need to check my times on that

---

