---
title: "Split file into smaller pieces"
date: 2010-01-22
forum: Desktop Environments
---

### Post by buster2209 on 2010-01-22
I have few a large media files (avi, mkv, etc) that I want to make into several smaller files as I cant transfer them to my external HD for storage as I get the error 'file is too large'. 

I then want to be able to copy the relevant files *back* to my internal HD and recombine them to make one big file that I can play.

How can I do this?

---

### Post by buster2209 on 2010-01-23
bump

---

### Post by howefield on 2010-01-23
Use the archive manager to create a split rar file which you can copy over , then decompress.

Are you using Karmic ?

Right click on the file and select compress, click the down arrow for "Other Options" and choose a format that will allow you to split the archive. As I said above rar is one of them, but there are others.

---

### Post by nmaster on 2010-01-23
it might be better to reformat your hd (maybe NTFS instead of FAT) so that you don't get an error.  i'm not sure how to answer your question though.

---

### Post by d3v1150m471c on 2010-01-23
> About splitSplit a file into pieces.
Syntax
*split [-linecount | -l linecount ] [ -a suffixlength ] [file [name] ]*
*split -b n [k | m] [ -a suffixlength ] [ file [name]]*
 -linecount | -l linecountNumber of lines in each piece. Defaults to 1000 lines. -a suffixlengthUse suffixlength letters to form the suffix portion of the filenames of the split file. If -a is not specified, the default suffix length is 2. If the sum of the name operand and the suffixlength option-argument would create a filename exceeding NAME_MAX bytes, an error will result; split will exit with a diagnostic message and no files will be created. -b nSplit a file into pieces n bytes in size. -b n kSplit a file into pieces n*1024 bytes in size. -b n mSplit a file into pieces n*1048576 bytes in size. fileThe path name of the ordinary file to be split. If no input file is given or file is -, the standard input will be used. nameThe prefix to be used for each of the files resulting from the split operation. If no name argument is given, x will be used as the prefix of the output files. The combined length of the basename of prefix and suffixlength cannot exceed NAME_MAX bytes; see OPTIONS.  Examples
**split -b 22 newfile.txt new** - would split the file "newfile.txt" into three separate files called newaa, newab and newac each file the size of 22.
**split -l 300 file.txt new** - would split the file "newfile.txt" into files beginning with the name "new" each containing 300 lines of text each


...okay wrapping is annoying

---

### Post by Mike_IronFist on 2010-01-23
> **neal.m.master said:**
> it might be better to reformat your hd (maybe NTFS instead of FAT) so that you don't get an error.  i'm not sure how to answer your question though.

Yeah, you need to know what kind of filesystem your HD uses. If it's FAT, you need to change it to NTFS - FAT filesystems do not allow files over 4 GB, while NTFS filesystems do.

---

### Post by buster2209 on 2010-01-23
Thanks for the split volume advice, I  will try it.

Yeah, I use FAT because I had soooooooooooo many problems with using NTFS.  Namely input/output errors when trying to move files from my external to my internal HD.

For reasons I don't understand, FAT seems a lot more stable.

---

