---
title: "Inrease partition after moving to a new hard-drive"
date: 2009-04-02
forum: General Help
---

### Post by blingo on 2009-04-02
Greetings all,

So I've got a slick new 500Gb hard-drive,
And passed all my previous 320Gb contents to it using Ghost 4 Linux.

Now I want to increase the _indows partition by that 180Gb, how do I do it?

(Normally I would do that the old trail and error method, but I'm a bit scared to do that now :redface:)

Thanks :-)

---

### Post by kanikilu on 2009-04-02
I'm a little confused as to what exactly you're trying to do, but generally speaking you can use gparted on the Ubuntu Live CD (or gparted Live CD) to resize existing partitions:

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

It should do this non-destructively, but of course it's always a good idea to have a current backup before doing anything to the partitions.

---

### Post by blingo on 2009-04-03
Solved!

So besides using gparted, I had to install 'ntfsprogs' which made  gparted capable of doing NTFS changes (otherwise I couldn't change the NTFS partition)

This what I've done, and the final result is also the wanted state:
The hard-drive looked like this:

_indows
Linux
free space

and I've wanted to increase the _indows partition
so I've moved the Linux to the end, to look like this:

_indows
free space
Linux

then increased the _indows partition:

_indows
Linux

Yippi!!!
Thanks :-)

P.S that gparted is a fine program...

A.P.S what happened to the 'Thanks' button?
and why can't I close the thread on Thread tools?

---

