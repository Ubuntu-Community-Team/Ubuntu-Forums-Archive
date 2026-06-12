---
title: "Apply offset to timestamps of multiple files"
date: 2009-02-24
forum: General Help
---

### Post by stefanadelbert on 2009-02-24
I have a number of digital photos (JPG's) that were taken before I realised that the camera's clock was incorrect. I would now like to apply a 45min offset to all the files, but can't think of a good way to do it.

One possible solution would involve looping through all the files, getting the current timestamp of each file, adding 45mins (the non-trivial part) and then changing the timestamp with touch.

Has anyone got any other suggestions? Maybe this can be done in Perl using a datetime module which would make adding the offset to each timestamp easier.

---

### Post by heindsight on 2009-02-24
If you want to change the file timestamps you can do something like:
```

#!/bin/sh

T=$(stat -c %y "$1")
NT=$(date -d "$T+45min" +%Y%m%d%H%M.%S)
touch -t "$NT" "$1"

```

This will set the access time and modification time of the file passed as argument to the old modification time +45mins

Keep in mind though that the file timestamps will change each time the file is accessed or modified. Also, this won't change the EXIF timestamps of the picture. To do that, you could install exiv2:
```
sudo apt-get install exiv2
```
and do:
```
exiv2 -a "+00:45" *.jpg
``` to add 45mins to the EXIF timestamps of all jpg files in the current directory.

**EDIT:** after setting the EXIF timestamps, you could also set the file access and modification times of each jpg to its EXIF timestamp by doing:
```
exiv2 -T *.jpg
```

---

### Post by stefanadelbert on 2009-02-24
Hey heindsight

Thanks for the input. I'll probably end up changing the modified and the EXIF timestamps using your advice.

Much appreciated.

Stefan

---

### Post by stani on 2009-06-27
Now you can also use Phatch for that:
[http://ubuntuforums.org/showthread.php?t=1178224](http://ubuntuforums.org/showthread.php?t=1178224)

---

