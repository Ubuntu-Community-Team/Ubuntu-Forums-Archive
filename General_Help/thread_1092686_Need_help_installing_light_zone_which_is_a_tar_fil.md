---
title: "Need help installing light zone which is a tar file"
date: 2009-03-10
forum: General Help
---

### Post by domromer on 2009-03-10
I downloaded a copy of light zone the raw editing software. It showed up as a tar.gz file. I did some research and figured out how to uncompress the folder, now I like to install it and I'm stuck. I have a linux book but it doesn't make it clear how to load this type of file and I've searched the threads here on the forum and I'm having some difficulty finding an answer.

I'm very new to Linux so a lot doesn't make sense to me yet. Thanks in advance for any help you can offer.

---

### Post by taurus on 2009-03-10
When you unpacked it, it would usually create a new directory.  Change to the new directory with the cd command and either look at the readme or INSTALL.  Otherwise, post the output of this command in that new directory.

```
ls -la
```

---

### Post by domromer on 2009-03-10
I gotta say your answer is a bit beyond me at this point. Could you break it down a bit for me.

---

### Post by taurus on 2009-03-11
Give me the link where you've downloaded it and I will walk you though it.

---

### Post by lightbots on 2009-03-22
/LightZone$ ls -la
total 16824
drwxr-xr-x 4      4096 2009-03-22 19:12 .
drwxr-xr-x 3      4096 2009-03-22 19:12 ..
-rw-r--r-- 1    502485 2008-08-14 20:28 dcraw
drwxr-xr-x 2      4096 2009-03-22 19:12 .install4j
-rw-r--r-- 1    531676 2008-08-14 20:28 jh.jar
drwxr-xr-x 4      4096 2009-03-22 19:12 jre
-rw-r--r-- 1   2308406 2008-08-14 20:28 lcjai.jar
-rw-r--r-- 1     60080 2008-08-14 20:28 libDCRaw.so
-rw-r--r-- 1    362713 2008-08-14 20:28 libFASTJAI.so
-rw-r--r-- 1    368473 2008-08-14 20:28 libfbf.so
-rw-r--r-- 1    143827 2008-08-14 20:28 libJAI.so
-rw-r--r-- 1     60468 2008-08-14 20:28 libLCArrays.so
-rw-r--r-- 1     74951 2008-08-14 20:28 libLCCache.so
-rw-r--r-- 1     52957 2008-08-14 20:28 libLCFileUtil.so
-rw-r--r-- 1     99859 2008-08-14 20:28 libLCJNI.so
-rw-r--r-- 1    907619 2008-08-14 20:28 libLCJPEG.so
-rw-r--r-- 1    666024 2008-08-14 20:28 libLCMS.so
-rw-r--r-- 1   1651118 2008-08-14 20:28 libLCTIFF.so
-rw-r--r-- 1     84352 2008-08-14 20:28 libLinux.so
-rw-r--r-- 1   3309314 2008-08-14 20:28 libmlib_jai.so
-rw-r--r-- 1    203080 2008-08-14 20:28 libSegment.so
-rw-r--r-- 1   3518619 2008-08-14 20:28 lightcrafts.jar
-rw-r--r-- 1     51208 2008-08-14 20:28 lightcrafts-linux.jar
-rwxr-xr-x 1      7761 2008-08-14 20:28 LightZone
-rw-r--r-- 1       952 2008-08-14 20:28 LightZone_16.png
-rw-r--r-- 1      2236 2008-08-14 20:28 LightZone_32.png
-rwxr-xr-x 1     17185 2008-08-14 20:28 LightZone-forkd
-rw-r--r-- 1   1066746 2008-08-14 20:28 lightzonehelp.jar
-rw-r--r-- 1     41500 2008-08-14 20:28 mlibwrapper_jai.jar
-rw-r--r-- 1     14732 2008-08-14 20:28 script-api.jar
-rw-r--r-- 1  965279 2008-08-14 20:28 substance-lite.jar

---

