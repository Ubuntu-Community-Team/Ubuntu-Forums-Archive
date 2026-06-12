---
title: "Printing in Acrobat Reader 7.0"
date: 2006-07-19
forum: Desktop Environments
---

### Post by LordMau on 2006-07-19
I'm having similar issue as in this [thread]("http://ubuntuforums.org/showthread.php?t=24420") at the hoary boards, but I'm using dapper.

In my case pdfs opened then printed via acroread always stall. What's maddening was just early this morning I had been printing via acroread with no problems at all. I've tried opening the same pdf file on evince then printed from there and it works.

Expanding on this, I've tracked down the temp .gs file in the spool directory of the pdf i've tried to print. Copied then opened the .gs file under ghostview to confirm it's the same file. Verifying so I then tried to print via commandline as noted above, in  my case I used the same command as indicated under acroread's print dialog:

```
lpr -P i255 -o Resolution=300x600dpi,PageSize=Letter *pdf-file.gs*
```

which fails. Tried also without the extra options. I've also checked htop and see two processes owned by cupsys which look stalled. I've attached an image for reference.

So any thoughts on how I can restore printing to acroread? Thanks

---

