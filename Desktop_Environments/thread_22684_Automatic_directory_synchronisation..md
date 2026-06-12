---
title: "Automatic directory synchronisation."
date: 2005-03-29
forum: Desktop Environments
---

### Post by lewiz on 2005-03-29
First off -- hi.  I'm fairly new to Ubuntu, only started using it about a month ago.  It's working out really well for me and I keep trying to get everybody else moved over :)  Good work to the developers!

I'm looking for a nice integrated way to synchronise a directory between two machines.  I have a number of "Places" set up (my laptop and a Windows share) and I'd like some way to say:  "Synchronise my downloads directory on this machine with this "Place"".

I suppose I'm looking for a frontend to unison or rsync.  Ideally it would offer options to ignore certain folders (I know unison can do this), detect when machines are available (even if it just polls periodically) and has a made where all local changes get propagated to the remote "Place" immediately.

This sure seems like a lot to want but most of it is absolute ideal.  Really a basic frontend to either of these tools is just what I'm after.

Any ideas at all would be greatly appreciated.  Thanks a lot!

---

### Post by tim1 on 2005-03-29
Maybe [iFolder](http://www.ifolder.com/) is just what your looking for.

It depends on mono and there are no debian packages available, that might be a showstopper for you.

greets, tim

---

### Post by kperkins on 2005-03-29
Have you tried unison-gtk?  It looks very basic, but may be just what you need. (Just apt-get it or use synaptic.)

---

### Post by lewiz on 2005-04-05
[QUOTE=tim1]Maybe [iFolder](http://www.ifolder.com/) is just what your looking for.[/QUOTE]

Sorry it took me so long to reply (my notifications aren't working (or I didn't set them up right ;)) -- I'm going to have a go at getting this working, it looks like what I'm after.  I'll get back here if I manage to get it working.
Thanks.

---

### Post by lewiz on 2005-04-09
Well, I've got iFolder installed and "working".
I made some very basic debs (they have no dependencies) which should work with any post-Hoary release (I think).  You can grab them from [http://noisy.compsoc.man.ac.uk/~lewiz/hoary/ifolder/](http://noisy.compsoc.man.ac.uk/~lewiz/hoary/ifolder/)
I can't really get it to do much -- maybe the Workgroup functionality is not yet implemented.  If anybody else can figure out how to use it let me know :)

---

### Post by adonet on 2007-12-30
Any chance that this program will be available for Ubuntu?

---

