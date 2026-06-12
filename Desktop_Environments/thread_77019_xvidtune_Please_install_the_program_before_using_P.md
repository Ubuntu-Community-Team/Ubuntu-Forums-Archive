---
title: "xvidtune Please install the program before using Part 2"
date: 2005-10-16
forum: Desktop Environments
---

### Post by korniko on 2005-10-16
The LCD screen ([www.mitac-europe.com](www.mitac-europe.com) Model MT-5120A-S Type FPD1520) is offset horizontally and tryed to run xvidtune but got "Please install the program before using". Traced reason to adInstalled flag but after setting this from true to false in /etc/X11/app-defaults made no progress. Ran out of Google help. Anyone got a neat solution to a horizontally shifted picture without adjusting the monitor as its OK under Win98SE and Mandrake 10.1 (Incidently using earlier Mandrakes we had to use xvidtune but not with 10.1 and later) Regards Korniko ubuntu 5.10
---
"Sound like something went wrong with the install, xvidtune should definitely be accessible by default.
Have you tried updating?" Darkmatter replied.
---
I tried updating and re-installing but it didn't change situation.
Note Eleaf also said "...so I found the program "xvidtune" wich is supposed to correct things like this. So I tried doing the command and it said, Please install the program before using it. But the program is installed. I tried reinstalling but it doesn't make a difference. However, when I launch this program on my iBook, it loads right up! I don't know why it would work on my ibook not my imac..." (subject: Monitor Correction)"

xvidtune always appeared accessible and judging from the below 'c' code the message is internally generated. 
[www.x.org/pub/unsupported/programs/xvidtune/xvidtune.c](www.x.org/pub/unsupported/programs/xvidtune/xvidtune.c)
if (!AppRes.ad_installed) {fprintf(stderr, "Please install the program before using\n"); return 3;}
Maybe an understanding of how the boolean ad_installed is set would clarify matters.
Anyway I cheated and installed kubuntu 5.10 Breezy Badger with kde and xvidtune runs fine without error messages and so did Left Left Left Apply and all is well.
Regards Korniko ex-ubuntu 5.10  now kubuntu 5.10

---

