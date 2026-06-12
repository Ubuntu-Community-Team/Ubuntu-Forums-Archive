---
title: "&quot;Dependency is not satisfiable&quot;"
date: 2009-04-11
forum: General Help
---

### Post by calvinps on 2009-04-11
Hello.

I am trying to install Yahoo! Messenger for Linux using a .deb package, but then an error comes up, saying:

[B][COLOR=Red][SIZE=3]Error: Dependency is not satisfiable: libglib1.2

[/SIZE][/COLOR][/B]I don't understand what that error means, but I am thinking that one of the dependencies is broken.

I got the package from [http://linux.softpedia.com/get/Communications/Chat/Yahoo-Messenger-002.shtml](http://linux.softpedia.com/get/Communications/Chat/Yahoo-Messenger-002.shtml).

---

### Post by taurus on 2009-04-11
Last Updated:  **June 15th, 2005**, 14:52 GMT  :shock:

Try using pidgin.

---

### Post by Wayne_V on 2009-04-11
last updated 2005 --- that's an antique!

Pidgin is much better anyway:

$ sudo apt-get install pidgin

---

### Post by calvinps on 2009-04-11
> **taurus said:**
> Last Updated:  **June 15th, 2005**, 14:52 GMT  :shock:

Try using pidgin.

I need a Yahoo Messenger-compatible app that supports Webcam. Can you think of any?

---

### Post by Wayne_V on 2009-04-11
kopete does I believe.   Ekiga maybe?

---

### Post by calvinps on 2009-04-11
> **Wayne_V said:**
> kopete does I believe.   Ekiga maybe?

Just about to try kopete, will post back if I like it ;D

---

### Post by bjackson on 2009-04-14
Im running into a problem getting my webcam to work with Kopete. Ive been trying to troubleshoot it, but am thinking i simply have to new of a webcam. I keep getting an error of:

I cannot find the jasper image convert program.

jasper is required to render the yahoo webcam images.

Please see [http://wiki.kde.org/tiki-index.php?page=Kopete%20Webcam%20Support](http://wiki.kde.org/tiki-index.php?page=Kopete%20Webcam%20Support) for further information. 

Ive been through what i can at that weblink, but am still having problems. Anyone know of another good troubleshooting help for Kopete?

b.

---

### Post by Wayne_V on 2009-04-14
So you did "sudo apt-get install libjasper-runtime" ?

You might want to install cheese ('sudo apt-get install cheese') just to test your webcam.

---

### Post by askreet on 2009-04-14
> **bjackson said:**
> Im running into a problem getting my webcam to work with Kopete. Ive been trying to troubleshoot it, but am thinking i simply have to new of a webcam. I keep getting an error of:

I cannot find the jasper image convert program.

jasper is required to render the yahoo webcam images.

Please see [http://wiki.kde.org/tiki-index.php?page=Kopete%20Webcam%20Support](http://wiki.kde.org/tiki-index.php?page=Kopete%20Webcam%20Support) for further information. 

Ive been through what i can at that weblink, but am still having problems. Anyone know of another good troubleshooting help for Kopete?

b.

It's probably better if you open a separate topic about that.  Someone may have already had the same issue but would not know to look here with a subject like "Dependency is not satisfiable".

Best of luck!
- askreet

---

