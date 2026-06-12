---
title: "Bulk Filename Changes"
date: 2006-08-21
forum: Desktop Environments
---

### Post by citizenkeith on 2006-08-21
I currently have a music library of 273 CDs in FLAC format. I started this project in windows, and used Album Art Aggregator to download all the covers. AAA's default file name is cover.jpg. Now that I'm on Ubuntu and more familiar with the "standards" of FLAC libraries, I would like to change them all to folder.jpg.

All the files are located at /media/windows2 (it's a FAT32 drive). Is there a command line I can use that will search recursively through that directory and change all instances of cover.jpg to folder.jpg?

---

### Post by waldschm on 2006-08-21
I'm not 100% sure about doing this since I haven't tried it, I just read an article about it: 
[http://www.linux.com/article.pl?sid=06/06/28/1541237](http://www.linux.com/article.pl?sid=06/06/28/1541237)

so maybe check that out for yourself, but it seems like something to this effect should work.

```
find /media/windows2 -name "cover.jpg" -exec mv "folder.jpg" {} \;
```

edit: might want to try adding the -i flag to mv first just in case

---

### Post by citizenkeith on 2006-08-22
Waldschm,

Thanks for the tip. I gave this a try, but it's not working. 

```
mv: cannot stat `folder.jpg': No such file or directory
```

I read through the article, and tried a few variations, but it's not working. If I use just this:

```
find /media/windows2 -name "cover.jpg" 
```

All the cover.jpg files are found. The problem seems to be with "-exec mv"

I'm inexperienced with the command line, and reading some articles online has confused me even more! :D Any other ideas?

Thanks folks.

---

### Post by waldschm on 2006-08-22
Hey I found a command that will probably work better. The rename command appears like it should do what you want using a perl expression but I don't have much experience with perl unfortunately. Try the man page:

```
man rename
```

---

### Post by Lunar_Lamp on 2006-08-22
I wrote a small script to do something similar to this a while ago (and a bit more).  Whilst there may be a clearer way from a syntax perspective, I think this would work:

```
find PATH/TO/UPPERMOST/DIRECTORY/SEARCHED/ | perl -ne'chomp; next unless -e; $oldname = $_; s/cover.jpg/folder.jpg/; next if -e; rename $oldname, $_'
```



That will, recursively, find all instances of "cover.jpg" and replace them with "folder.jpg".  You should CERTAINLY test this out first - just create a folder with copies of 2 or 3 of your albums in it and run the command to make sure it will do what you want.

---

### Post by citizenkeith on 2006-08-22
Thanks Lunar_Lamp. That did the trick! :) Now I'll read up on all the codes to see how it was done.

---

