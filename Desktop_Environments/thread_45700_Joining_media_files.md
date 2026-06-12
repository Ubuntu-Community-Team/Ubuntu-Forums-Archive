---
title: "Joining media files"
date: 2005-07-01
forum: Desktop Environments
---

### Post by jcooper on 2005-07-01
If I have two large (~700mb each) avi files, is there any way I can join them to create one large file?

I've had a look on the internet and there doesn't seem to be any way to use built in filesystem functions - cp, mv, cat all seem to generate dud files.

**EDIT**: I've found a random forum posting stating the use (for e.g.) of:

```
cat input_1.avi input_2.avi | mencoder -noidx -ovc copy -oac copy -o
output.avi -
```
**UPDATE**: FYI anyone that's interested and wants to achieve the same: [http://itdp.fh-biergarten.de/~itdp/html/mplayer-users/2005-02/msg00404.html](http://itdp.fh-biergarten.de/~itdp/html/mplayer-users/2005-02/msg00404.html)

All of these people appear to encounter problems. Does anyone have a bulletproof method?!

---

### Post by jcooper on 2005-07-01
Update - I've just found [avifile-utils](http://packages.debian.org/unstable/graphics/avifile-utils).

I'm hoping the debian package will work - though will check to see if there's a corresponding Ubuntu version when I'm home this evening.

It appears to depend on a QT application, which I'm assuming in turn will depend on various KDE libs.

Anyone know of a standalone tool?

---

### Post by jcooper on 2005-07-01
A script to do the job, providing mplayer is installed:

[http://community.moertel.com/ss/space/Tom%27s+Bash+shell+code/join-avi-files](http://community.moertel.com/ss/space/Tom%27s+Bash+shell+code/join-avi-files)

---

### Post by omegasoul on 2005-07-03
I have found that the best solution is to use hjsplit through wine.

---

### Post by jcooper on 2005-07-04
It appears they have a GTK+ (v1) version for Linux.

[http://estudiantes.univalle.edu.co/~juanjmed/gtklxsplit/GTKlxsplit.html](http://estudiantes.univalle.edu.co/~juanjmed/gtklxsplit/GTKlxsplit.html)

---

### Post by dakine on 2005-12-01
avimerge -o output.avi -i input1.avi input2.avi

about the simplest way to join avi files in linux

dakine

---

