---
title: "Help"
date: 2008-12-21
forum: General Help
---

### Post by mondy on 2008-12-21
After install wine,i got this problem:[/media/cdrom0/setup.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /media/cdrom0/setup.exe or
          /media/cdrom0/setup.exe.zip, and cannot find /media/cdrom0/setup.exe.ZIP, period.Can anyone help? thanks:):)

---

### Post by w0ng on 2008-12-21
Rather than double-clicking the exe file in the cd drive folder, run it as wine through Terminal or Alt+F2
```
wine /media/cdrom0/setup.exe
```

---

