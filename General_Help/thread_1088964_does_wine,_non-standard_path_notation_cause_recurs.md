---
title: "does wine, non-standard path notation cause recursion problems for scp, tar?"
date: 2009-03-06
forum: General Help
---

### Post by sloggerkhan on 2009-03-06
I am just curious, I have been working on backing up a bunch of my files from my desktop via scp and tar, and the way I calculate it, combined size of all files I'm backing up shouldn't have exceeded 1.1 terabytes, but it looks like it is starting to exceed by relatively more.

First it was a 'huh'? thing, but watching stuff go by on command line in tar and scp, I keep seeing a lot of entries
```

backup_home_20090212/.wine/dosdevices/z:/lib/udev/devices/fd/3/backup_home_20090212/....

```

which leaves me to believe that somehow the z:/ thing leading to recursive copying of some sort of link from the wine filesystem...

I'm probably going to just stop all transfers and start over, but is there an option to prevent this? I'm not sure that it's using standard links, as I don't recongize z: notation as part of a path.

I may just delete .wine, there's no reason to even back it up, I use wine maybe every several months for one game.

My worry, though, is that there may be something besides the .wine directory I don't know about causing some sort of recursive copy problem. How would I detect this?

---

### Post by snova on 2009-03-06
I saw something like this recently, I think the problem was that there is a symlink within ~/.wine that points to /- so you're actually backing up your entire system. And there are apparently a few recursive symlinks scattered around.

The links are in ~/.wine/dosdevices, where each link points to another "device" for the exported Windows filesystem. Try temporarily moving this directory somewhere that isn't being backed up.

---

### Post by sloggerkhan on 2009-03-07
yeah, there's some sort of a recursive loop using scp with .wine directory... 
I nuked the .wine folder and about 96% of the space I was using got freed up.

PAIN IN THE BUTT!!

---

