---
title: "Mirroring my files, monitoring the mirror for changes"
date: 2009-03-16
forum: General Help
---

### Post by teachmeifyoucan on 2009-03-16
Hi,

I have a large collection of MP3 files that I'd like to _mirror_ onto an external hard drive for backup purposes.

Rather than create a tarball or other large file container, I simply want to duplicate (copy) all files onto the external HD.

Because my MP3 collection changes and grows, I am looking for a program that is capable of comparing the mirror to the original (when I tell it to) and updating the mirror to match the original. If I add a file to the original, the software should copy the file to the same location within the mirror. And if I delete a file from the original, the software should also delete the corresponding file from the mirror.

If no free software exists that is capable of doing this, I am willing to purchase such a program. However, it must be capable of running under the Ubuntu system, because I don't want to be forced to use Wine.

Thanks in advance for all pointers!

---

### Post by jonobr on 2009-03-16
have you tried investigating rsync?

Its lightweight and easy to use and script.
You can have it as complicated as you want it to be

heres a bit of blurb , first one from google

[Rsync]("http://http://www.fredshack.com/docs/rsync.html")

or just type man rsync on your system.. I think its there by default

---

### Post by binbash on 2009-03-16
Grsync

---

### Post by jonobr on 2009-03-16
fair point, thats rsync with a fancy dress on:-)

---

### Post by teachmeifyoucan on 2009-03-17
Beautiful! Thanks, guys!

---

