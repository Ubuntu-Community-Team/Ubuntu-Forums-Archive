---
title: "error: setting up alien arena"
date: 2006-06-06
forum: Gaming &amp; Leisure
---

### Post by ELD on 2006-06-06
Hi all trying to setup alien arena and i get this:
> 
liam@ubuntu:~$ chmod +x alienarena-2006-x86.run
liam@ubuntu:~$ ./alienarena-2006-x86.run
Verifying archive integrity... All good.
Uncompressing Alien Arena 2006: Uranium Edition for Linux..........................................................................................
/home/liam/.setup5890: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory


Any ideas what i do to fix that error?

Many thanks!

---

### Post by Harleen on 2006-06-06
You need to install the old gtk library.
```
sudo apt-get install libgtk1.2
```

---

### Post by ELD on 2006-06-06
Will it overwrite my current one?

---

### Post by Harleen on 2006-06-06
No, it installs libgtk 1.2 besides gtk 2.0. Nothing to worry about.

---

### Post by ELD on 2006-06-06
Thanks, works perfectly, thanks a bunch!

---

### Post by RotoGrip on 2006-06-09
Im starting to hate Dapper, never had the problems with Breezy like i do now. Trying to install this game as well and i get 2 diffrent errors.

jeff@jeff-home:~/Desktop$ ./alienarena-2006ue-x86.run
Verifying archive integrity... All good.
Uncompressing Alien Arena 2006: Uranium Edition for Linux.................................................................................
gzip: stdin: invalid compressed data--crc error

gzip: stdin: invalid compressed data--length error
Extraction failed.

OR

jeff@jeff-home:~/Desktop$ ./alienarena-2006ue-x86.run
Verifying archive integrity...Error in MD5 checksums: 20daa1dc6f4f9ac99b8c04d4befd9077 is different from c14015339572adf6062612bd1f01e1cb

Any help with the above?

Thanks

---

### Post by siriusnova on 2006-06-09
[QUOTE=RotoGrip]Im starting to hate Dapper, never had the problems with Breezy like i do now. Trying to install this game as well and i get 2 diffrent errors.

jeff@jeff-home:~/Desktop$ ./alienarena-2006ue-x86.run
Verifying archive integrity... All good.
Uncompressing Alien Arena 2006: Uranium Edition for Linux.................................................................................
gzip: stdin: invalid compressed data--crc error

gzip: stdin: invalid compressed data--length error
Extraction failed.

OR

jeff@jeff-home:~/Desktop$ ./alienarena-2006ue-x86.run
Verifying archive integrity...Error in MD5 checksums: 20daa1dc6f4f9ac99b8c04d4befd9077 is different from c14015339572adf6062612bd1f01e1cb

Any help with the above?

Thanks[/QUOTE]

The file you downloaded is corrupted, bad mirror maybe? The MD5 checksum is basically like a key that the file has and is used to verify wether a file corrupted or not.

---

### Post by RotoGrip on 2006-06-09
Yeah, i tried all 3 mirrors that were available and i get the same crap. Had this problem with ET, and ETF as well.

---

### Post by mithras86 on 2006-06-12
But on most systems, ET works really good. In 8 seconds, i'll give a try to AA2K6. I think you have to look at your internetconnection or something.

---

