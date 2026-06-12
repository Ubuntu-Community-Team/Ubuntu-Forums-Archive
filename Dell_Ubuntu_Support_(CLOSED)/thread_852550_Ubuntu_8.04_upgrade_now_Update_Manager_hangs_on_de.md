---
title: "Ubuntu 8.04 upgrade now Update Manager hangs on dell inspiron 530"
date: 2008-07-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by LesFromWaldenVT on 2008-07-07
For a few weeks now, since I upgraded to 8.04, the Update Manager sits with an hourglass (spinning circle or whatever) forever (or until I kill it).

Any idea what might be wrong? It says I have 173 updates to do. I'd like to do them.

Thanks,
Les

I should add that I have a working broadband connection.

---

### Post by LesFromWaldenVT on 2008-09-02
Well, I fixed it myself. It turns out that using the command line:

>sudo apt-get update
>sudo apt-get upgrade -y -u

did the trick. There must have been some problem in the graphical version.

---

