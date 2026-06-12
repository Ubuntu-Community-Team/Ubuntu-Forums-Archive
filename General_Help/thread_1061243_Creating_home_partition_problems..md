---
title: "Creating /home partition problems."
date: 2009-02-05
forum: General Help
---

### Post by spaceship.rodeo on 2009-02-05
Hey all.  I've been putting off creating a seperate partition for /home for a while now and I figured I'd give it a shot today.  So I went and made a livecd and followed [this](http://www.psychocats.net/ubuntu/separatehome) guide and it went pretty well up until I had to use the command line.  I believe this is the line that won't work:
```
sudo find . -depth -print0 | cpio --null --sparse -pvd /new/
```

When I try to use it, it just says permission is denied for everything it tries to copy or whatever it's doing (I'm not quite sure).  Now I was thinking about installing a different distro, so I thought I'd just instead of trying to do that stuff, I'd just back all my personal files up onto my windows partition and just copy and paste them back into my new /home.  

So I tried booting up my regular ubuntu install and it won't let me.  It says there's no /home directory now and will log me out as soon as I try to log in.  I haven't tried logging on to windows and seeing if I can access my stuff from there, but I figured I'd ask and see if anyone here can help me first, just in case.

---

### Post by Iowan on 2009-02-05
I noticed a note that might be helpful:> Note: I have tested the second command myself, and it works, but some have pointed out it might make sense to [COLOR="Red"]preface the commands with sudo[/COLOR] in case one of the other users has subdirectories manually marked as unreadable to the user making the move. Since I have not tested this out and all directories and readable to all by default, I'm offering this as only an alternative in case the command as given does not work:
[COLOR="Red"]sudo find . -depth -print0 | sudo cpio --null --sparse -pvd /new/[/COLOR] 

---

