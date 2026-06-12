---
title: "Syncronize directories in 3 machines"
date: 2009-05-12
forum: General Help
---

### Post by LucaTNT on 2009-05-12
Hi everyone!
I have 2 computers at home, both with Kubuntu Jaunty and a "server", a NSLU2 with Debian, which exports a 500G drive on my network through NFS.

I want to keep my music collection on all of them: I need it on the computers for local playback and on the "server" because it's accesed by my PS3 through UPNP.

I would like that whenever I add some files/folders on any of these 3 machines they are synchronized with the other 2 (through a daily cronjob if possible).

I already use rsync to backup /home, but AFAIK the synchronization is one way only.

Any advice?
Thanks in advance.

---

### Post by LucaTNT on 2009-05-12
I managed to do this with [Unison](http://www.cis.upenn.edu/~bcpierce/unison/).

You just have to run:
```
unison /path/to/folder/on/machine1 /path/to/folder/on/machine2
```
for first time indexing and then run this command in your cronjob:
```
unison -batch /path/to/folder/on/machine1 /path/to/folder/on/machine2
```

---

