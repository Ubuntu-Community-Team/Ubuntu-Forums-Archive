---
title: "automatix screwed up my apt-get"
date: 2006-07-14
forum: Desktop Environments
---

### Post by k420 on 2006-07-14
while installing java from automatix it came to a spot where hit enter to try again or hit no+ enter to cancel. it halts on sun-java7-doc sayin that i need to download some java file. it wont let me upgrade install remove or anything.  What can i do so it doesnt keep trying to install this truthfully i dont want the doc files for java anyway

---

### Post by k420 on 2006-07-14
here is the actual error 
```
Setting up sun-java5-doc (1.5.0-06-1) ...
This package is an installer package, it does not actually contain the
J2SDK documentation.  You will need to go download one of the
archives:

    jdk-1_5_0-doc.zip jdk-1_5_0-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    http://java.sun.com/j2se/1.5.0/download.html

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] no
Abort installation of J2SDK documentation
dpkg: error processing sun-java5-doc (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 sun-java5-doc
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

