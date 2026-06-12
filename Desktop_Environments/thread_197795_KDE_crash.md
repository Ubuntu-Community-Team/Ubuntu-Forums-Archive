---
title: "KDE crash"
date: 2006-06-16
forum: Desktop Environments
---

### Post by RoNoVe on 2006-06-16
When I startup kde from withing either kdm or gdm, kde starts up, and right when it gives me the tingeling-sound, it blacks out, and crashes..
I removed kde, reïnstalled it, same error..

My .xsession-errors file which was generated when starting kde from within gdm can be found at [http://pastebin.com/712852](http://pastebin.com/712852)

Anyone can help me to localise and squash the error?

thx in advance
--
Ilias

---

### Post by pyromithrandir on 2006-06-16
Have you tried using a different user account to see if the problem is system wide or confined to some bad settings in your home directory?

---

### Post by RoNoVe on 2006-06-17
I only have one account, but I'm going to reïnstall kde and first delete my .kde settings

---

### Post by RoNoVe on 2006-06-17
and it worked :)

I deleted
-/etc/kde3
-/home/ilias/.kde/

Then reinstalled, but had to manually extract /etc/kd3/kdm/ out of the archive and copy it there..

And bam, it worked :)

---

