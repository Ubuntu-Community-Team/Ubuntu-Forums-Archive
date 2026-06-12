---
title: "Terminal: Recursive copying"
date: 2009-01-04
forum: General Help
---

### Post by Johnaspire on 2009-01-04
Wondering if its possible to recursively copy all the files of a certain type to another place in the terminal.

My specific example:  Copy all *.jpg files from my harddrive to a usb drive.

---

### Post by unutbu on 2009-01-04
```
rsync -avm --include='*.jpg' -f 'hide,! */' /path/to/source/ /path/to/destination
```

Be sure to keep the forward-slash (/) at the end of "/path/to/source/", otherwise the copy will be placed at /path/to/destination/path/to/source instead of /path/to/destination.

(See
[http://ubuntuforums.org/showthread.php?t=954164](http://ubuntuforums.org/showthread.php?t=954164))

---

### Post by kaibob on 2009-01-04
```
find /source/directory -name '*.jpg' -type f -exec cp '{}' /destination/directory ';'
```

Change /source/directory and /destination/directory. If the destination directory is on an external usb hard drive, the destination directory would be something like /media/drive/directory.

---

