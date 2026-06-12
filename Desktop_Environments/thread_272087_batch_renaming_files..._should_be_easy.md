---
title: "batch renaming files... should be easy"
date: 2006-10-05
forum: Desktop Environments
---

### Post by yeehawjared on 2006-10-05
so I have a folder containing 100 mp3s.  They look like this:

001 - Artist - Title With Spaces.mp3
002 - Artist - Another song.mp3
...
100 - Artist - Last Song.mp3

How can I rename every file so it'll be:

2005-001 - Artist - Title With Spaces.mp3
2005-002 - Artist - Another song.mp3
...
2005-100 - Artist - Last Song.mp3


I've been playing around with commands listed on this page, editing them to do what I want.
[http://lab.artlung.com/unix-batch-file-rename/](http://lab.artlung.com/unix-batch-file-rename/)
All I want to do is add the 2005-  string.  How can I do this?  Thanks guys. :D

---

### Post by mitch.c on 2006-10-05
> **yeehawjared said:**
> I've been playing around with commands listed on this page, editing them to do what I want.
[http://lab.artlung.com/unix-batch-file-rename/](http://lab.artlung.com/unix-batch-file-rename/)
All I want to do is add the 2005-  string.  How can I do this?  Thanks guys. :D
The rename you are trying to complete should be pretty simple with the rename command, like this:
```
rename 's/(^.*$)/2005-$&/' *.mp3
```
Try it.

---

### Post by yeehawjared on 2006-10-06
awesome.  I'll try when I get home.  Thanks :D

---

### Post by aysiu on 2006-10-06
If you prefer a point-and-click method, you can also use KRename, which is in the repositories.

---

