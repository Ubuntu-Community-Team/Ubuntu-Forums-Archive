---
title: "ps2pdf stopped working! help please"
date: 2009-03-18
forum: General Help
---

### Post by quantumstitch on 2009-03-18
ps2pdf just stopped working today. latex and dvips work fine. but running ps2pdf foo.ps foo.pdf produces:

```
Error: /undefined in obj
Operand stack:
   2   0
Execution stack:
   %interp_exit   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--   --nostringval--   --nostringval--   false   1   %stopped_push   1905   1   3   %oparray_pop   1904   1   3   %oparray_pop   1888   1   3   %oparray_pop   1771   1   3   %oparray_pop   --nostringval--   %errorexec_pop   .runexec2   --nostringval--   --nostringval--   --nostringval--   2   %stopped_push   --nostringval--
Dictionary stack:
   --dict:1151/1684(ro)(G)--   --dict:0/20(G)--   --dict:71/200(L)--   --dict:186/300(L)--   --dict:43/200(L)--
Current allocation mode is local
Last OS error: 2
Current file position is 175218
GPL Ghostscript 8.63: Unrecoverable error, exit code 1
```

Please help.

```

sudo apt-get install --reinstall texlive-base-bin
```
did nothing.

--stitch

---

### Post by nmaster on 2009-07-03
i have a slightly different error, but it seems very similar. 
[http://ubuntuforums.org/showthread.php?p=7554860#post7554860](http://ubuntuforums.org/showthread.php?p=7554860#post7554860)

any help would be great.

---

### Post by Chronon on 2009-07-03
I can't help with this problem (didn't know about it until now).  However, dvipdf is working fine.  If you're creating PS first with dvips and then converting to PDF why not just run dvipdf instead?

Maybe this isn't helpful, but I wanted to point out another path exists to produce PDFs if that's all you care about.

Actually, I just tested and can't reproduce this error.  I ran dvips to get a postscript version of my document and then ps2pdf and it didn't throw any errors.  The resulting PDF looks just how it should.

---

