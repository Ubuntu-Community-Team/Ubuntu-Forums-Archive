---
title: "Issues with Team Fortress 2 dedicated server on Ubuntu 12.04"
date: 2012-08-19
forum: Gaming &amp; Leisure
---

### Post by RichardCozODST on 2012-08-19
So I installed Ubuntu 12.04 on a minimal image (so I can run it on a Terminal without any GUI) and downloaded the files for a dedicated server on Linux for Team Fortress 2.  When I run the command ./srcds_run (with other parameters) I get a segmentation fault when the game tries to start.

I was informed to run ldd for the binary and it says it's missing libtier0.so and libvstdlib.so, which are in the /orangebox/bin directory to begin with, so I don't know why it's not recognizing the two files.

What should I do about this issue?

---

### Post by Perfect Storm on 2012-08-20
Can you please give the ldd report of the binary?

It may that those libs are either misplaced or there's a script to run the server that tells where to look for the libs.

---

### Post by sandyd on 2012-08-23
Weird

I just installed ia32libs, and followed these two guides (though no new user - this was a VM)

The only difference is that I used
```
./steam -command update -game tf -dir .
```
instead of installing in a seperate folder.

That could be it. 
[http://wiki.teamfortress.com/wiki/Linux_dedicated_server](http://wiki.teamfortress.com/wiki/Linux_dedicated_server)
[http://tf2wiki.net/wiki/Linux_dedicated_server](http://tf2wiki.net/wiki/Linux_dedicated_server)

---

### Post by RichardCozODST on 2012-09-21
Sorry with a late response.  I haven't checked on my server desktop on this case.  The weird part is that when I ran ldd on the Left 4 Dead 2 server (which was just recently), there's nothing wrong there.  I'll try updating TF2 and see what happens.  If the problem persists, I'll make the next post.

---

