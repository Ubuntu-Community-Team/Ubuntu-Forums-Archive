---
title: "How to install J2SE Runtime Environment (JRE) with Plug-in for Mozilla Firefox?"
date: 2005-12-29
forum: General Help
---

### Post by Rhizome21 on 2005-12-29
hey i'm trying to download this via [http://java.sun.com/j2se/1.5.0/download.jsp](http://java.sun.com/j2se/1.5.0/download.jsp) but it says that the site is busy. What is going on, is there another site where it has it. ? :mad:

---

### Post by Odinist on 2005-12-29
Have you tried installing and using Automatix to do it for you?

---

### Post by Rhizome21 on 2005-12-29
im in the U.S, it's illegal to do through automatix :S

---

### Post by ykpaiha on 2005-12-29
if it's forbidden in Us then the rest of the world.....sorry it was just a thought

check in the howto you will get easy way to turn this out ,without the american way of life as well (lol)

---

### Post by Odinist on 2005-12-29
The only part of Automatix that is "illegal" is installing the "non-free" audio and dvd codecs.

---

### Post by Rhizome21 on 2005-12-29
I can't seem to install automatix :-\ 
```
alvaro@alvaro:~$ wget -c  http://ubuntuforums.org/attachment.php?attachmentid=3447&d=1131494867
--16:05:05--  http://ubuntuforums.org/attachment.php?attachmentid=3447
           => `attachment.php?attachmentid=3447'
Resolving ubuntuforums.org... [1] 6983
alvaro@alvaro:~$ 64.21.33.9
Connecting to ubuntuforums.org|64.21.33.9|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

100%[====================================>] 31,592        54.67K/s

16:05:06 (54.57 KB/s) - `attachment.php?attachmentid=3447' saved [31592]

tar xzf automatix-ubuntu_v3.1.tar.gz
tar: automatix-ubuntu_v3.1.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
[1]+  Done                    wget -c http://ubuntuforums.org/attachment.php?attachmentid=3447

```

---

### Post by Odinist on 2005-12-30
Hrm... Try this.

Open Firefox, and go to this URL:

[http://beerorkid.com/automatix/automatix-ubuntu_4.2-1_i386.deb](http://beerorkid.com/automatix/automatix-ubuntu_4.2-1_i386.deb)

Choose to save the file to your Home folder. Next, open a terminal window and (making sure your working directory is your Home folder) type:

sudo dpkg -i automatix-ubuntu_4.2-1_i386.deb

---

