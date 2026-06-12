---
title: "script"
date: 2009-05-12
forum: General Help
---

### Post by wrathkeg on 2009-05-12
Hi,  I have a command which finds (recursively) all files with a particular set of characters in the filename:
```
find . -name foo\*.avi
```
I want to combine the files which are found using mkvmerge, which has the following syntax:
```
mkvmerge foo1.avi foo2.avi -o combined.mkv
```
Can anyone tell me how to combine these two commands into one, or into a script?  I'm sure it must be possible to have the results of the first command as input to the second, but can't figure it out!
WK

---

### Post by kpkeerthi on 2009-05-12
```

find . -name foo\*.avi -print0 | xargs -0 mkvmerge -o combined.mkv

```

---

### Post by ibuclaw on 2009-05-12
Try:
```
find . -name "foo*.avi" | xargs -0 -I"{}" mkvmerge {} -o combined.mkv
```


Regards
Iain

---

### Post by wrathkeg on 2009-05-12
that's what i call a quick response! thanks!
wk

---

