---
title: "How to use wget to download a single webpage?"
date: 2006-08-07
forum: Desktop Environments
---

### Post by geuis on 2006-08-07
I want to have my machine grab a copy of a webpage and store it locally. So far the wget commands I've used download the entire site and all its subfolders. I just want to have it download the single page and not follow all the sub links.

This is what I've had that mirrors everything:

wget --mirror –p --HTML-extension –-convert-links –P \wget_files\example1 [http://www.yourdomain.com](http://www.yourdomain.com)

I guess ideally I would just like it to save 1 index.html file w/ the supporting images. Can I change this wget command to do it?

---

### Post by aysiu on 2006-08-07
Try this: ```
wget -r -l 1 http://www.yourdomain.com
```

---

### Post by cantormath on 2006-08-07
> **geuis said:**
> I want to have my machine grab a copy of a webpage and store it locally. So far the wget commands I've used download the entire site and all its subfolders. I just want to have it download the single page and not follow all the sub links.

This is what I've had that mirrors everything:

wget --mirror –p --HTML-extension –-convert-links –P \wget_files\example1 [http://www.yourdomain.com](http://www.yourdomain.com)

I guess ideally I would just like it to save 1 index.html file w/ the supporting images. Can I change this wget command to do it?
a few ideas

(cd cmdline && wget -nd -pHEKk [http://www.pixelbeat.org/cmdline.html](http://www.pixelbeat.org/cmdline.html))	Store local browsable version of a page to the current dir
 	wget -c [http://www.example.com/large.file](http://www.example.com/large.file)	Continue downloading a partially downloaded file
 	wget -r -nd -np -l1 -A '*.jpg' [http://www.example.com/](http://www.example.com/)	Download a set of files to the current directory
 	wget [ftp://remote/file](ftp://remote/file)[1-9].iso/	FTP supports globbing directly
•	wget -q -O- [http://www.pixelbeat.org/timeline.html](http://www.pixelbeat.org/timeline.html) | grep 'a href' | head	Process output directly
 	echo 'wget url' | at 01:00	Download url at 1AM to current dir
 	wget --limit-rate=20k url	Do a low priority download (limit to 20KB/s in this case)
 	wget -nv --spider --force-html -i bookmarks.html	Check links in a file
 	wget --mirror [http://www.example.com/](http://www.example.com/)	Efficiently update a local copy of a site (handy from cron)

---

### Post by geuis on 2006-08-08
Hey, I think I got it. Awesome.

One more question, right now the remote website is being saved in the same directory where my php file is. How can I make it save the remove websites in a sub directory?

---

### Post by aysiu on 2006-08-09
```
cd *subdirectory*
wget -r -l 1 http://www.nameofsite.com
```

---

### Post by geuis on 2006-08-09
How do I do it in the same wget command. I might also be running this through a php script.

---

### Post by geuis on 2006-08-10
For future reference if anyone with this problem is looking for the answer, you can specify the save path with -Ppath/to/folder

Its in the format of -P followed by the directories. Has to be attached to -P and not separate like -P path/to/folder

---

