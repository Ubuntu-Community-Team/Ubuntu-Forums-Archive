---
title: "Prevent gvfs from starting"
date: 2009-11-28
forum: Desktop Environments
---

### Post by akudewan on 2009-11-28
Hi,

I was using Gnome earlier, but then I installed kubuntu-desktop. I liked it, so I started using KDE.

When I insert a USB drive, it gets mounted, but I cannot unmount it in KDE if gvfs is running in the background. If the gvfs daemons are killed before mounting the drive, things work fine.

Is there any way I can prevent gvfs from starting? It's Gnome-specific and I can do without it, right?

Thanks!

(PS: Using Karmic and KDE 4.3 from the kubuntu ppa)

---

### Post by akudewan on 2009-11-29
*bump*

---

### Post by Zorael on 2009-11-29
I don't have it installed, though I know that keeping it that way has been something of a chore, since a lot of packages recommend GNOME-specific stuff that you have to explicitly opt out of installing alongside your wanted package (gvfs being no exception).

You should be able to do without it. Try removing it and see what it says.
```
$ sudo aptitude remove gvfs -P
```

---

### Post by akudewan on 2009-11-29
Thanks for replying.

A lot of packages depend of gvfs, some of which I use. So uninstalling wasn't really an option. I want to keep Gnome installed for now.

After a lot of digging around, I did manage to find a workaround:
Create a file named .xsessionrc in the $HOME directory with the following contents:
```

#!/bin/bash
GVFS_DISABLE_FUSE=1
export GVFS_DISABLE_FUSE

```
(Might need to do a chmod +x as well)

After restarting the X session, the ~/.gvfs thingy isn't mounted, and my USB thumb drive mounts/unmounts properly in KDE. gvfsd is still running in the background, but doesn't seem to be causing any trouble.

(PS: Zorael - It was because of some of your posts and your sig that I decided to try out KDE again :) )

---

### Post by mardukvmbc on 2010-04-30
> **akudewan said:**
> Thanks for replying.

A lot of packages depend of gvfs, some of which I use. So uninstalling wasn't really an option. I want to keep Gnome installed for now.

After a lot of digging around, I did manage to find a workaround:
Create a file named .xsessionrc in the $HOME directory with the following contents:
```

#!/bin/bash
GVFS_DISABLE_FUSE=1
export GVFS_DISABLE_FUSE

```
(Might need to do a chmod +x as well)

After restarting the X session, the ~/.gvfs thingy isn't mounted, and my USB thumb drive mounts/unmounts properly in KDE. gvfsd is still running in the background, but doesn't seem to be causing any trouble.

(PS: Zorael - It was because of some of your posts and your sig that I decided to try out KDE again :) )

No joy. Absolutely love KDE but need dropbox and hence need nautilus too... if anyone has a fix please let me know!

---

### Post by NissePisse123 on 2010-06-27
This is what worked for me:
```
gconftool --type Boolean --set /apps/nautilus/preferences/media_automount  false
```

See also: [https://help.ubuntu.com/community/Mount/USB]("https://help.ubuntu.com/community/Mount/USB")

---

### Post by mardukvmbc on 2010-06-28
thanks man!

---

### Post by Trenchbroom on 2010-07-07
> **NissePisse123 said:**
> This is what worked for me:
```
gconftool --type Boolean --set /apps/nautilus/preferences/media_automount  false
```

See also: [https://help.ubuntu.com/community/Mount/USB]("https://help.ubuntu.com/community/Mount/USB")

Worked like a charm--thanks!

---

