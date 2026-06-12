---
title: "My frost wire doesn't work, gives me a jre message"
date: 2006-10-07
forum: Desktop Environments
---

### Post by thenetduck on 2006-10-07
Hi, 
  I am trying to download and use Frost Wire but every time I try to run it via terminal.... frostwire it gives me this message. 



```

Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at http://www.java.com
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://www.java.com
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://www.java.com
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://www.java.com




```



I have all ready downloaded the jre 5.0 with Automatix2 Can somone assist me in getting this to work? Thank you ,
 The Net Duck

---

### Post by taurus on 2006-10-07
At the prompt, what is the output of this command then?

```
java -version
```

---

### Post by thenetduck on 2006-10-07
Hi sorry for the delayed reply, 

 
outputs this...


java version "1.4.2"
gij (GNU libgcj) version 4.1.0 (Ubuntu 4.1.0-1ubuntu8)

Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.



The Net Duck

---

### Post by taurus on 2006-10-07
You need to install a copy if Java either from Sun or Blackdown.  You can use either Automatix or BUMPS to install it if you wish...

[http://www.ubuntuforums.org/showthread.php?t=181251](http://www.ubuntuforums.org/showthread.php?t=181251)

---

