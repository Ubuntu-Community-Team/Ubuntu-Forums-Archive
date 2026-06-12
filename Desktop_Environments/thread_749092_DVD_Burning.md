---
title: "DVD Burning"
date: 2008-04-08
forum: Desktop Environments
---

### Post by smoove on 2008-04-08
I've got k3b and Brasero installed, but I think they both require an ISO to be created before it can actually burn the movie so I can watch it on my dvd player downstairs. 

How do i convert my .avi files to .iso files? 

Thanks.

---

### Post by MeURi on 2008-04-08
Wait a sec :-)

ISO image creation is an optional step, you can actually burn your files (not only movies) directly to cd/dvd.

The question is: do you want to burn a dvd containing a movie (like you would do for backup purpose), or a video dvd?

See [thread=218165]this thread[/thread] for references, if you stick with k3b ;-)

For Brasero, I don't know much about it, but since you have also k3b installed... :-P

---

### Post by smoove on 2008-04-08
Direct video dvd, so it plays straight off downstairs like a normal dvd would. 

Seems i gota convert them to iso first?! :-(

EDIT: When i try accesing synaptic it tells me:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: _cache->open() failed, please report.

When i run that command in terminal is states that I need to be a superuser to execute, when I'm the only default user/admin already?

---

### Post by kpkeerthi on 2008-04-08
You should run it with **sudo** prefixed
```
sudo dpkg --configure -a
```

---

### Post by smoove on 2008-04-08
Thanks for that! I done the command it worked fine, looks like something didnt finish of installing vmware, is that why it would have broke?

Also it toke several minutes for it to work again after i entered the command, why would there be a delay?

---

### Post by kpkeerthi on 2008-04-08
Yeah. It would take sometime scanning the dependency tree in the package database and make sure the dependencies exist as it should, if not fix it.

---

### Post by trippinnik on 2008-04-08
You can try Devede.  Very easy to use program for making DVDs from avi.  It will make either the .iso or the VIDEO_TS AUDIO_TS necessary to make a playable dvd.

---

