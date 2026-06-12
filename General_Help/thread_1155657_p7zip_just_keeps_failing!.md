---
title: "p7zip just keeps failing!"
date: 2009-05-11
forum: General Help
---

### Post by Miles_Prower on 2009-05-11
I've been trying to tar and compress my stuff so I can put it on this ftp/samba server I just set up, so I looked to 7zip (as I'd recently noticed that 7zip can turn 9 GB of files into 1GB). Tar itself seemed to take the filesize of my video folder down from 75 GB to 8 GB, which frightens and confuses me, as I'm not entirely convinced that TAR is supposed to compress. I though it was just supposed to... tar files together? Maybe tar failed? It didn't give any error message.... Anyways, I tried to 7zip the tar file for good measure and when I run p7zip from the command line, the terminal will keep on truckin' 'till it just hits this error:

```
knuklz@lava_reef:/media/disk$ p7zip video.tar

7-Zip (A)  4.58 beta  Copyright (c) 1999-2008 Igor Pavlov  2008-05-05
p7zip Version 4.58 (locale=en_US.UTF-8,Utf16=on,HugeFiles=on,1 CPU)
Scanning

Creating archive video.tar.7z

Compressing  video.tar

System error:
E_FAIL

```



E_FAIL? that's right up there with PC load letter.

Am I doing it wrong? These files are pretty large, maybe it just takes too long and 7zip times out?

---

### Post by baseface on 2009-05-11
after you tarred your video directory, did you untar it to see if everything was still the same?
```
tar xvf whatever.tar
```

---

### Post by Miles_Prower on 2009-05-11
ran tar again with the verbose option (-v). Failed again, but transferred the same ammount of bits. looks like there's a file in there that tar can't handle.

//edit

Uh... hmm.... Seems like tar fails after 4096 bits... moar testing required.

---

### Post by Miles_Prower on 2009-05-12
uh, TAR keeps failing now. I've been getting the error
Wrote only 4096 of 10240 bytes
relatively consistently, even though I've been trying to tar different folders. Also, can I change the name of this thread?

---

