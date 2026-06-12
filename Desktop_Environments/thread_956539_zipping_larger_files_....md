---
title: "zipping larger files ..."
date: 2008-10-23
forum: Desktop Environments
---

### Post by asearle on 2008-10-23
Hallo All,

I have been trying to compress (zip) a directory full of large files (each about 2Gb) with a total size of almost 8Gb.

I have been trying to do this with ARK but it seems to always crash (leaving a temp file of 2Gb size).

There isn't much of an error message and so I am not sure why it is crashing (is there a log file somewhere?) but my suspicion is that there is a limit to the size of files that can be zipped.

Under Windows I find that, with 7zip, I can zip these files.  But ARK won't do it.

Can anyone help me here?  Is there an alternative tool that I could use?  Or are there settings that I should change in ARK?

Many thanks for any tips that you can give me.

Regards,
Alan

---

### Post by SamNSane on 2008-10-23
Forgive me for asking, but I'll post the obvious question -- the location where you are trying to create the archive, what file system is it?

---

### Post by snova on 2008-10-23
Hooray for 7zip! Unfortunately the nice GUI that comes with 7zip hasn't been ported to Linux.

7zip works from the command line. The worst that can happen is that you'll get more helpful error messages. Try:

```
7z a archive.7z directory
```

Add -mx=9 to the line for better compression. Actually 7zip has probably a dozen options to increase the compression level, but not all of them play well with 1 gigabyte of ram. :)

---

