---
title: "Now trying to get the necessaries for wmv files"
date: 2006-07-28
forum: Desktop Environments
---

### Post by elbowgeek on 2006-07-28
First, a big thanks to all who've helped me recently as I get my dear old Samsung A10 up to fighting shape with Ubuntu.

The problem I now have is getting wmv files to play.  I followed the instructions [here]("https://help.ubuntu.com/community/RestrictedFormats#head-6c942d1939d97331f96e42b63774003fde7daed5"), but the output of the commands mentioned on the page is:
```

elbowgeek@elbowgeek-laptop:~$ wget -c http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20060611-0.0_i386.deb
--04:56:49--  http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20060611-0.0_i386.deb
           => `w32codecs_20060611-0.0_i386.deb'
Resolving www.debian-multimedia.org... 213.186.33.16
Connecting to www.debian-multimedia.org|213.186.33.16|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://www.debian.org [following]
--04:56:50--  http://www.debian.org/
           => `index.html'
Resolving www.debian.org... 194.109.137.218
Connecting to www.debian.org|194.109.137.218|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 14,841 (14K) [text/html]

100%[====================================>] 14,841        41.09K/s

04:56:53 (40.90 KB/s) - `index.html' saved [14841/14841]

elbowgeek@elbowgeek-laptop:~$ sudo dpkg -i w32codecs_20060611-0.0_i386.deb
Password:
dpkg: error processing w32codecs_20060611-0.0_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 w32codecs_20060611-0.0_i386.deb
```

Is there something I'm doing wrong here, or is there some other method of retrieving the codecs I need?


Many thanks

---

### Post by patrickthebold on 2006-07-28
You have the wrong URL.  I dunno the right URL but the wget command failed so the .deb package never downloaded.

---

### Post by elbowgeek on 2006-07-28
Hmm, interesting.  I checked the site referred to in the first command, and the files are definitely where they should be. In any case, I've started downloading them manually, so we'll see how they install.

Cheers

---

### Post by Hikaru79 on 2006-07-28
There is a known problem with trying to wget the files. If you just open it in a regular browser and download the .deb manually, it works perfectly.

---

### Post by elbowgeek on 2006-07-28
That did it.

---

### Post by Danny Boy on 2006-07-29
I had the same problem.. searched and found this thread, fixed perfectly. Thanks :)

---

