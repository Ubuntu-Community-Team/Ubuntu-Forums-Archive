---
title: "Shell Script"
date: 2009-03-19
forum: General Help
---

### Post by bradthewanderer on 2009-03-19
I am trying to write my first shell script to find files older than 90 days and delete them, I was wondering if anyone can point me in the right direction?

Thanks

---

### Post by aeiah on 2009-03-19
if you want this as an exercise, then basically you'll need a script that finds things older than 90 days with the find command, and then uses the rm command to remove the files it returns.


[or you could cheat](http://www.howtogeek.com/howto/ubuntu/delete-files-older-than-x-days-on-linux/)

---

### Post by bradthewanderer on 2009-03-19
Thank you so much for the exercise it led me to my answer. :)

---

### Post by bradthewanderer on 2009-03-19
Anyone have a good basic list of books that can help a beginner Shell Scripter learn? 

Thanks

---

### Post by geirha on 2009-03-19
The Advanced Bash-Scripting Guide at [http://tldp.org/guides.html](http://tldp.org/guides.html) is quite good. Lots of examples.

---

### Post by fieroboom on 2009-03-19
Just a note of caution... Be sure you define paths where there are no system files. In other words, **don't** tell your script to rm -rf /
because that will delete everything in the root directory, which is, well, everything. In fact, everything you delete should most likely be in /home/<your_username>/
:D
-Paul

---

### Post by Tek-E on 2009-03-19
A great shell scripting book to look for is "Shell Scripting Recepies."  It is more of an Advanced users book. But even a beginner could learn alot of information from it! Great Book!~

---

### Post by cmay on 2009-03-19
> **bradthewanderer said:**
> Anyone have a good basic list of books that can help a beginner Shell Scripter learn? 

Thanks

o reily has a book called classic shell scripting which is a heavy book and the parts i read is detailed but not designed to be casual reading. its a bit hard to read i think but i have no doubt that the one who wants to learn somthing can use it for learning shell scripting. its not what i call a beginners book.

 if you happen to find a copy of the book the unix programming environment by brian w kernighan there is a chapter on shell programming and there is lots of other useful things in this book other than c programming which is the reason i have read it.

---

### Post by bradthewanderer on 2009-03-20
Thanks to all of you for answering my questions. However I have one more for you, what version of Bash is being used in Ubuntu 8.10?

---

### Post by sisco311 on 2009-03-20
> **bradthewanderer said:**
> Thanks to all of you for answering my questions. However I have one more for you, what version of Bash is being used in Ubuntu 8.10?

```
bash --version
``` ;)

---

### Post by geirha on 2009-03-20
[http://packages.ubuntu.com/search?keywords=bash&searchon=names&exact=1&suite=all&section=all](http://packages.ubuntu.com/search?keywords=bash&searchon=names&exact=1&suite=all&section=all)

---

### Post by bradthewanderer on 2009-03-20
Thank you very much all :).

---

