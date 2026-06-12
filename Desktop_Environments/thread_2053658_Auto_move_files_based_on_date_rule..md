---
title: "Auto move files based on date rule."
date: 2012-09-05
forum: Desktop Environments
---

### Post by zippyties on 2012-09-05
I am looking to make a script which will automatically move all files with today's date to a mounted FTP drive.  I am thinking that I will schedule the script to run everyday at night and upload all files with today's date.

I know almost nothing about scripting in Linux.  I am fairly proficient in the terminal.

Where would be a good starting point for this kind of task?

---

### Post by drmrgd on 2012-09-05
Would these files be modified today, accessed today, or just actually have today's date as part of the name?  I'm not sure the best way to do this, but you could potentially use the *time option of find (-mtime = modified time, -atime=accessed time) and then pass it to an exec function of find.  

Maybe something along the lines of:

```
find /path/to/files -mtime 1 -exec mv "{}" /path/to/move/files/to \;
```

Just to verify it's finding the correct files, you should probably leave out the -exec bit to confirm it's behaving as you wish.

Here's an excellent tutorial on how to use time queries in find to do specific tasks that I've referenced a bunch in the past:

[http://www.cyberciti.biz/faq/howto-finding-files-by-date/](http://www.cyberciti.biz/faq/howto-finding-files-by-date/)

I'm sure the real bash masters here will probably have a slicker way to do this, though.

---

