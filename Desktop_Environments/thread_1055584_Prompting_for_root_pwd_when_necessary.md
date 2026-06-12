---
title: "Prompting for root pwd when necessary"
date: 2009-01-30
forum: Desktop Environments
---

### Post by ayampanggang on 2009-01-30
Hello all!

I'm wondering if it's possible to pop up the gksu / kdesudo / kdesu when needed.

For example, I suddenly want to copy a file from my home folder to somewhere outside e.g. /usr/local/bin

When i ctrl+c ctrl+v the file from my home to /usr/local/bin, a dialog box prompting for root password appears, and copying would only be successful if i entered the right password.

I looked at kde-apps.org but best I could find is an additional context menu: "copy as root/ move as root" which would make my context menu ugly :( 

Oh and I use dolphin in kde 4 with debian/gnu linux, but i think a solution should apply anywhere (with necessary modification)

Thank you very much!

---

### Post by x33a on 2009-01-30
open a terminal, type gksudo nautilus or dolphin or thunar. with this you can copy/move your files as a super user.

---

### Post by ayampanggang on 2009-05-29
Yeah it can work like that too, but I just wonder if I can pop the box only when needed, it will feel more streamlined.

Anybody knows how?

Sorry for the so so late reply.

---

