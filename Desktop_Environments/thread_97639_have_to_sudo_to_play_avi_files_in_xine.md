---
title: "have to sudo to play avi files in xine"
date: 2005-12-01
forum: Desktop Environments
---

### Post by otake-tux on 2005-12-01
couple of days ago I could play anything in xine with no problem.  Now if I try to pay an avi file without typing sudo first I get this error:
```
The Stream 'path to file I tried to play' use an unsupported codec:
Video Codec: XviD (XVID)
Start playback anyway?
```
if I click yes I get sound but no visual.  Now I thought that somehow the codec got errased :???: 
but when I  type
```
sudo xine /path to file/file.avi
```
it plays with no problems.
maybe its a permissions error.......
what do you guys think?

---

### Post by itwasi on 2005-12-20
I have this same issue.  It worked  one moment then suddenly I couldn't play wmv or avi files.  They do start when using the terminal.  Is there any solution?

---

