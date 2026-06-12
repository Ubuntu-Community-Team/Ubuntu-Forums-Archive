---
title: "Singularity Errors Out On Latest LTS Ubuntu"
date: 2016-08-14
forum: Desktop Environments
---

### Post by yogich246 on 2016-08-14
Singularity requires i386 libs, on 12.04, but they are included, in 16. Still, I get the following, when running as indirectly as can be done:

```

yogich@HP:~$ Singularity-x86_64-1.8.6.6157/singularity
Running from /home/yogich/Singularity-x86_64-1.8.6.6157
 - Installing menu entries in /home/yogich/.local/share/applications
Singularity-x86_64-1.8.6.6157/singularity: line 162: bin/singularity-do-not-run-directly: cannot execute binary file: Exec format error
*** Bad shutdown. ***

```
The desktop link doesn't work, either, of course. I'll be 1/2 way there, if I can get Singularity, working (see [Aside]).
--
[Aside] I much prefer, Ubuntu, but interestingly, it (and Blender) runs on latest Suse but that flavor won't run my MP4 video tutorials. Ubuntu will play my MP4s, but won't run Singularity (or Blender, either).   I mean, c'mon! :( (Of course, Blender, is for another topic.)

[16AUG16]
I discovered that Singularity does, indeed, work on the Ubuntu 16.04.1 Live DVD, but not, on the installed, system. (Blender, latest, copies, this behavior.) That is just, wrong. If it works on Live DVD, it must work on the installed, system. Anything less, is wasting one's time.

Even UNetBootin can't help, with this, because its persistent space is not saving anything I put, there. I put a small file, on it, rebooted, and it was gone.  Sourceforge is completely silent, on its use, too, so that is no help. In 8 pages of reviews, the persistent space was mentioned a single time, in passing.

---

