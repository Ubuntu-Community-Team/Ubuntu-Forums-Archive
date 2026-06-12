---
title: "How to mux avi and srt files"
date: 2006-02-22
forum: Desktop Environments
---

### Post by jimscullion on 2006-02-22
Can anyone suggest how to do this in Breezy?  I know that submux will do it for mpg and srt, but not for avi and srt.

Thanks in advance.

Jim

---

### Post by jimscullion on 2006-02-23
bump

---

### Post by jamesford on 2006-05-22
found a solution:

mencoder -vop pp=de,scale=608:336 -oac copy -ovc lavc -lavcopts vhq:vqmin=2:vqmax=2:vme=1:keyint=25:vbitrate=2140:vpass=1 -sub "SUBTITLE_FILE.srt" -o "OUTPUT_MOVIE_WITH_SUBTITLES.avi" "SOURCE_MOVIE.avi"

---

