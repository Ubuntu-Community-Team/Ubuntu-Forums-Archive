---
title: "7za is crashing ubuntu"
date: 2006-08-16
forum: Desktop Environments
---

### Post by fakie_flip on 2006-08-16
Every time I run 7za to try to compress these files, my computer freezes, and I have to reboot. That happened many times. I can not move my mouse for a long time. Below shows that I tried creating many 7z files, but my computer crashed before they could be finished. Someone asked me if my computer crashed or if my cpu was just running at 100%. I don't know. I couldn't move my mouse for a while, so I restarted the computer.

```
ubuntu@ubuntu:~/Desktop/A$ ls -lh
total 37G
-rw-r--r-- 1 ubuntu ubuntu   32 2006-08-15 16:04 archive.7z
-rw-r--r-- 1 root   root    12M 2006-08-15 02:56 archive.7z.tmp
-rw-r--r-- 1 ubuntu ubuntu    6 2006-08-15 02:32 foo
-rw-r--r-- 1 ubuntu ubuntu  113 2006-08-15 02:34 foo.7z
-r--r--r-- 1 ubuntu ubuntu 2.4G 2006-07-23 00:31 Music2.tar
-rw-r--r-- 1 ubuntu ubuntu 7.1M 2006-08-15 16:13 Music2.tar.7z
-r--r--r-- 1 ubuntu ubuntu 358M 2006-07-23 00:21 Music3.tar
-r--r--r-- 1 ubuntu ubuntu  13G 2006-07-25 10:27 S2_1.tar
-r--r--r-- 1 ubuntu ubuntu 8.9G 2006-07-25 10:27 S2_1.tar.bz2
-rw------- 1 root   root   2.9G 2006-08-15 02:56 S2_2.tar
-r--r--r-- 1 ubuntu ubuntu 9.5G 2006-07-25 19:32 S2_2.tar.bz2
ubuntu@ubuntu:~/Desktop/A$
```

I am using a command from one of the examples in the man page for 7za because I do not understand all of the options. I am using this.
```
EXAMPLE 1
       7za a -t7z -m0=lzma -mx=9 -mfb=64 -md=32m -ms=on archive.7z dir1
              adds all files from directory "dir1" to archive archive.7z using "ultra settings"

       -t7z   7z archive

       -m0=lzma
              lzma method

       -mx=9  level of compression = 9 (Ultra)

       -mfb=64
              number of fast bytes for LZMA = 64

       -md=32m
              dictionary size = 32 megabytes

       -ms=on solid archive = on


```

The difference is that I am not compressing a directory like that example. I do want to use these.

```
       -t7z   7z archive

       -m0=lzma
              lzma method

       -mx=9  level of compression = 9 (Ultra)

```

I am not sure what the other options are for, and if I need them, but I've been using them.

---

### Post by michux on 2006-08-16
Does your problem concern these certain files only or is it a general problem with that 7z syntax? 
Have you tried using another compression tool like bzip or is there a reason to use 7z instead?

---

### Post by fakie_flip on 2006-08-16
> **michux said:**
> Does your problem concern these certain files only or is it a general problem with that 7z syntax?

It's a general problem that happens no matter what files I try to compress. 

> **michux said:**
> Have you tried using another compression tool like bzip or is there a reason to use 7z instead?

Yes, I'm using 7za for a specific reason instead of bzip2. It has support for an algorithm with a very high compression ratio. I haven't found anything better. Here's what the man page says about it.

```
DESCRIPTION
       7-Zip  is a file archiver with the highest compression ratio. The program supports 7z (that implements LZMA compression algorithm), ZIP, CAB, ARJ,
       GZIP, BZIP2, TAR, CPIO, RPM and DEB formats. Compression ratio in the new 7z format is 30-50% better than ratio in ZIP format.

```

---

