---
title: "7zip Commands Needed!"
date: 2009-04-26
forum: General Help
---

### Post by Rytron on 2009-04-26
Hi.
I need a 7z command that will create a storage(no compression) level archive with a password.

I also need a 7zip command line to create a maximum compression archive with a password.
I've created this line. Does it look correct?
```
7z a -p -t7z /home/username/Desktop/cba.7z /home/username/Desktop/cba -mx9
```

Thanks.

---

### Post by albinootje on 2009-04-26
> **Rytron said:**
> 
```
7z a -p -t7z /home/username/Desktop/cba.7z /home/username/Desktop/cba -mx9
```


According to the manual page of 7z it looks pretty good, although this looks a bit nicer :
```

7z a -p -t7z -mx9 /home/username/Desktop/cba.7z /home/username/Desktop/cba

```
And I assume that the parameter -mx0 will let 7z not compress at all.

---

### Post by Rytron on 2009-04-26
Thanks.

I tried this. It seems to have zero compression. Does it look correct?
7z a -p -t7z /home/username/Desktop/folder1.7z /home/username/Desktop/folder1 -mx0

---

### Post by Rytron on 2009-04-27
Here are notes I've made on 7 Zip Commands. I'd appreciate it if anyone can confirm they are correct or if they can provide improvents to them. Here they are:

> ARCHIVE WITH MAXIMUM COMPRESSION
7z a -t7z -mx9 /home/username/Desktop/folder1.7z /home/username/Desktop/folder1

ARCHIVE WITH MAXIMUM COMPRESSION WITH PASSWORD
7z a -p -t7z -mx9 /home/username/Desktop/cba.7z /home/username/Desktop/cba
# p: password will be prompted for

ARCHIVE WITH NO COMPRESSION
7z a t7z -mx0 /home/username/Desktop/cba.7z /home/username/Desktop/cba

ARCHIVE WITH NO COMPRESSION WITH PASSWORD
7z a -p -t7z -mx0 /home/username/Desktop/cba.7z /home/username/Desktop/cba

EXTRACT ARCHIVE
7z x stuff.7z
OR
p7zip -d stuff.7z

COMPRESSION SWITCHS
-mx0 Don't compress at all. Is called "copy mode."
-mx1 Very low compression. It is called "fastest" mode.
-mx3 Fast compression mode. Will set various parameters automatically.
-mx5 Same as above, but "normal."
-mx7 "maximum" compression.
-mx9 "ultra" compression. You probably want to use this.

---

### Post by Rytron on 2009-09-05
Confirmed to work!

---

### Post by nomnex on 2009-12-03
you are using 7za (p7zip-full)

if you are using 7zr (p7zip) the commands are slightly different, but compression switches are identical.

max compression '-mx9' is buggy with folders containing many files. version 9.04 address the issue. it's available here [html]http://packages.debian.org/sid/i386/p7zip/download[/html] Tested on Jaunty.

7zr does not have a -p switch at my knowledge

EDIT:```
7z a archive myfolder
```will output the same result as below since it's default

```
7z a -t7z archive.7z myfolder 
```and Pass protected

```
-mhe=on|off (encrypt file headers in addition of -p{password})
```

---

### Post by Rytron on 2009-12-04
Thank you nomnex.

;)

---

