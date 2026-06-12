---
title: "How to get finer granularity in Ubuntu's file creation/modification timestamps?"
date: 2008-12-14
forum: General Help
---

### Post by ts509 on 2008-12-14
I'm a half-a-dozen-years Linux user, but so far I never needed a timestamp resolution finer than 1 second. But now I do.

**The Background**

An application is using Ghostscript to create individual JPEG-pages from PDF files. Each PDF input file gets its own subdirectory where all the JPEGs get archived. 

Other scripts continuously monitor that sub-directory and waits for the last page to be converted to JPEG. As soon as the last page is arrived they need to further process the JPEGs.

Ghostscript creates on average 2-3 pages/JPEGs per second. However, some PDF pages may need 2-3 minutes to be converted to JPEG. And some PDFs can't be fully converted at all. In which case another script is called to deal with that situation.

For performance (and debugging) reasons, a timely discovery of the latest created JPEG page is crucial. The scripts basically use the shell command [FONT="Courier New"]"ls -ltr subdir/*.jpeg|tail -n1"[/FONT] to do that.

Until last week, an old SuSE 9.1 system served as an NFS sharing storage system that held the JPEGs. It worked well enough for a good 4 years.

Yesterday, I exchanged the old box against an Ubuntu ruth server rented from an ISP running Intrepid. Now the problem starts....

**How to reproduce**

```
ruth@Ubuntu-810-intrepid-64-minimal:~/tmp> uname -a
Linux Ubuntu-810-intrepid-64-minimal 2.6.27-9-server #1 SMP Thu Nov 20 22:56:07 UTC 2008 x86_64 GNU/Linux

ruth@Ubuntu-810-intrepid-64-minimal:~/tmp> mkdir tst-timestamps

ruth@Ubuntu-810-intrepid-64-minimal:~/tmp> time for i in $(seq -w 1 100); do touch tst-timestamps/p00000${i}.jpeg ; done

real    0m0.079s
user    0m0.030s
sys     0m0.020s
ruth@Ubuntu-810-intrepid-64-minimal:~/tmp> ls -ltr tst-timestamps/*.jpeg | tail -n 10
-rw-r--r-- 1 ruth ruth 0 2008-12-14 21:52 tst-timestamps/p00000080.jpeg
-rw-r--r-- 1 ruth ruth 0 2008-12-14 21:52 tst-timestamps/p00000079.jpeg
-rw-r--r-- 1 ruth ruth 0 2008-12-14 21:52 tst-timestamps/p00000078.jpeg
-rw-r--r-- 1 ruth ruth 0 2008-12-14 21:52 tst-timestamps/p00000077.jpeg
-rw-r--r-- 1 ruth ruth 0 2008-12-14 21:52 tst-timestamps/p00000076.jpeg
-rw-r--r-- 1 ruth ruth 0 2008-12-14 21:52 tst-timestamps/p00000075.jpeg
-rw-r--r-- 1 ruth ruth 0 2008-12-14 21:52 tst-timestamps/p00000074.jpeg
-rw-r--r-- 1 ruth ruth 0 2008-12-14 21:52 tst-timestamps/p00000073.jpeg
-rw-r--r-- 1 ruth ruth 0 2008-12-14 21:52 tst-timestamps/p00000072.jpeg
-rw-r--r-- 1 ruth ruth 0 2008-12-14 21:52 tst-timestamps/p00000071.jpeg

ruth@Ubuntu-810-intrepid-64-minimal:~/tmp> ls -ltr --full-time tst-timestamps/*.jpeg |tail -n 10
-rw-r--r-- 1 ruth ruth 0 2008-12-14 21:52:41.000000000 +0100 tst-timestamps/p00000080.jpeg
-rw-r--r-- 1 ruth ruth 0 2008-12-14 21:52:41.000000000 +0100 tst-timestamps/p00000079.jpeg
-rw-r--r-- 1 ruth ruth 0 2008-12-14 21:52:41.000000000 +0100 tst-timestamps/p00000078.jpeg
-rw-r--r-- 1 ruth ruth 0 2008-12-14 21:52:41.000000000 +0100 tst-timestamps/p00000077.jpeg
-rw-r--r-- 1 ruth ruth 0 2008-12-14 21:52:41.000000000 +0100 tst-timestamps/p00000076.jpeg
-rw-r--r-- 1 ruth ruth 0 2008-12-14 21:52:41.000000000 +0100 tst-timestamps/p00000075.jpeg
-rw-r--r-- 1 ruth ruth 0 2008-12-14 21:52:41.000000000 +0100 tst-timestamps/p00000074.jpeg
-rw-r--r-- 1 ruth ruth 0 2008-12-14 21:52:41.000000000 +0100 tst-timestamps/p00000073.jpeg
-rw-r--r-- 1 ruth ruth 0 2008-12-14 21:52:41.000000000 +0100 tst-timestamps/p00000072.jpeg
-rw-r--r-- 1 ruth ruth 0 2008-12-14 21:52:41.000000000 +0100 tst-timestamps/p00000071.jpeg
```

As you can see, the *time resolution granularity* on this very recent Ubuntu system is only in **1 second steps**. That's the reason, why "ls -ltr" does not work as expected on Ubuntu. It means that the last expected JPEG is never-ever discovered, because the discovery command always shows the one of the files that were created in the same second, but are sorted in reverse alpabetic order to the one wanted.

Now see what the result of the same set of commands is on the old SuSE-9.1 box. This is how I'd expect it to work:

```
ruth@p15159123:~/tmp> uname -a
Linux p15159123 2.6.11.9-20050513151705 #1 SMP Mon May 16 02:24:22 IST 2005 i686 i686 i386 GNU/Linux

ruth@p15159123:~/tmp> ls -ltr tst-timestamps/*.tif|tail -n 10
-rw-r--r--  1 ruth ruth 0 2008-12-14 21:52 tst-timestamps/p00000091.tif
-rw-r--r--  1 ruth ruth 0 2008-12-14 21:52 tst-timestamps/p00000092.tif
-rw-r--r--  1 ruth ruth 0 2008-12-14 21:52 tst-timestamps/p00000093.tif
-rw-r--r--  1 ruth ruth 0 2008-12-14 21:52 tst-timestamps/p00000094.tif
-rw-r--r--  1 ruth ruth 0 2008-12-14 21:52 tst-timestamps/p00000095.tif
-rw-r--r--  1 ruth ruth 0 2008-12-14 21:52 tst-timestamps/p00000096.tif
-rw-r--r--  1 ruth ruth 0 2008-12-14 21:52 tst-timestamps/p00000097.tif
-rw-r--r--  1 ruth ruth 0 2008-12-14 21:52 tst-timestamps/p00000098.tif
-rw-r--r--  1 ruth ruth 0 2008-12-14 21:52 tst-timestamps/p00000099.tif
-rw-r--r--  1 ruth ruth 0 2008-12-14 21:52 tst-timestamps/p00000100.tif

ruth@p15159004:~/tmp> ls -ltr --full-time tst-timestamps/*.tif|tail -n 10
-rw-r--r--  1 ruth ruth 0 2008-12-14 21:52:59.586086925 +0000 tst-timestamps/p00000091.tif
-rw-r--r--  1 ruth ruth 0 2008-12-14 21:52:59.589086401 +0000 tst-timestamps/p00000092.tif
-rw-r--r--  1 ruth ruth 0 2008-12-14 21:52:59.591086052 +0000 tst-timestamps/p00000093.tif
-rw-r--r--  1 ruth ruth 0 2008-12-14 21:52:59.593085703 +0000 tst-timestamps/p00000094.tif
-rw-r--r--  1 ruth ruth 0 2008-12-14 21:52:59.596085179 +0000 tst-timestamps/p00000095.tif
-rw-r--r--  1 ruth ruth 0 2008-12-14 21:52:59.599084655 +0000 tst-timestamps/p00000096.tif
-rw-r--r--  1 ruth ruth 0 2008-12-14 21:52:59.601084305 +0000 tst-timestamps/p00000097.tif
-rw-r--r--  1 ruth ruth 0 2008-12-14 21:52:59.604083781 +0000 tst-timestamps/p00000098.tif
-rw-r--r--  1 ruth ruth 0 2008-12-14 21:52:59.606083432 +0000 tst-timestamps/p00000099.tif
-rw-r--r--  1 ruth ruth 0 2008-12-14 21:52:59.609082908 +0000 tst-timestamps/p00000100.tif

```

As you can see, the *time resolution granularity* on the 5 year old SuSE-9.1 system is in **1 NANOsecond steps**. Therefor "ls -ltr" works as expected.

My guess is that this very rude granularity in timestamps used in Ubuntu breaks a lot (a lot more than just mine) legacy scripts and applications that rely on  "reverse sort by timestamp".

**Now my questions:**

[LIST]
[*]What's the root cause to that different behavior between 4 year old SuSE 9.1 and 2 month old Ubuntu Intrepid?
[*]Do I need to compile my own custom kernel in order to get a better-than-1-second granularity for timestamps?
[*]If so, which parameters for configuring that kernel build do need to set?
[*]Or is that something I could configure in the currently running kernel, maybe inside the shell?
[*]If so, how?
[/LIST]

---

