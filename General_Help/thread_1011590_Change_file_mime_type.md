---
title: "Change file mime type?"
date: 2008-12-14
forum: General Help
---

### Post by newbjeff on 2008-12-14
Hi everyone,

I downloaded a series of RAR archive files, some of which are correctly identified in Hardy as archives, while others attempt to open with gedit.  Is there any application that would allow me to change the mime type of those that are wrong?  

Thanks,

Jeff

---

### Post by sedawk on 2008-12-14
I'm not sure that problem is related to mime stuff.

What happens if you run the tool "file" on a rar file that
is properly detected as rar file and one that is detected as not
being a rar file? Does "file" show different content?

```

$ file somearchive.zip
somearchive.zip: Zip archive data, at least v1.0 to extract
$ ...

```

---

### Post by newbjeff on 2008-12-16
OK,

An archive returns the file name followed by:

RAR archive data, v14, flags: Archive volume, os: Win32

the other file simply reports the file name:  data

Of the 30 or so files, the first seven came through as archives.

Thanks,

Jeff

---

