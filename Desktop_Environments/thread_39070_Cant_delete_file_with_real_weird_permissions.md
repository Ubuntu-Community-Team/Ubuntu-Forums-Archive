---
title: "Cant delete file with real weird permissions"
date: 2005-06-03
forum: Desktop Environments
---

### Post by Dogmeat on 2005-06-03
Hello, today i was going to start mozilla-firefox as usual, but it started then quit many times with all users, i think it was a problem with nphelix.so. So I removed mozilla-firefox with snaptic, then i went to remove the plugins (lots of broken symlinks) and reinstall firefox. But suddenly something real strange happened: I cant delete nphelix.so even as root!  checking out the file what do I see?

```
?---------  17299 root 31120 1142255176 1974-04-12 17:46 nphelix.so

``` 

what the fsck? I even tried rebooting through a RIP (recovery is possible) cd-rom and deleting that file but it says  operation not permitted all the time whatever I try to do to remove the file, anyone knows how to fix this? maybe edit the filesystem itself or something, i cant reinstall firefox (at least through synaptic) ultil I remove this  ](*,)

---

### Post by Dogmeat on 2005-06-03
well indeed I fsck'd it and i guess my HD is about to go to the other side. I'm thinking of moving my entire partition to my other hard drive, now to find out which grub files I should change...

---

### Post by Takis on 2005-06-03
[QUOTE=Dogmeat]```
?---------  17299 root 31120 1142255176 1974-04-12 17:46 nphelix.so

```[/QUOTE]
Dude that's awesome, congrats on getting a totally rooted [Edit: no pun intended] file! That must have taken some serious effort and you are to be commended.
```

$ ls -l nphelix.so
-rw-r--r--  1 root root 35560 2004-11-02 01:33 nphelix.so
$
```
The fact that it's supposedly 1.1GB and dated from 1974 probably isn't too good. Did you have any problems with Helix Player (nphelix.so is a Helix Player file). Did you have any power outages at any time? Seems something went funny and got past journaling too.

---

### Post by apswartz on 2005-06-03
try this as root...
chmod a+rw nphelix.so

then see if you can  delete it.

---

### Post by Dogmeat on 2005-06-03
[QUOTE=Takis]Dude that's awesome, congrats on getting a totally rooted [Edit: no pun intended] file! That must have taken some serious effort and you are to be commended.
[/QUOTE]

Props go to the harddrive, it's dying slowly I did a forced FSCK and there were loads of errors, miraculously I could still boot and most things still work (at least the few I tried). Good ol FSCK removed the weird file  :) 

I'll move this partition as soon as I format my other hard drive, can't wait to have Ubuntu on AT133 at 7200 rpm  :grin:

EDIT: I just copied my ubuntu partition with parted and changed the menu.lst accordingly. It works  like a charm now  :grin:

---

