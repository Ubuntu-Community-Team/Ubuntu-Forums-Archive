---
title: "Mounting, e2fsck question"
date: 2008-09-07
forum: Desktop Environments
---

### Post by idyllhands on 2008-09-07
Hello, I just bought a used laptop and decided to try out Ubuntu on it (Hardy Heron)  I'm new to Linux, but not computers.

I've been searching for several hours on info on this, and am not coming back with adequate help (besides finding a bunch of articles I don't understand and websites wanting to sell me a windows file system repair software)

I got it all installed, and ran a "badblocks" on it and got a list of several bad blocks, and I want to make it so these blocks aren't used for my data storage.

I think my next step is to run e2fsck -c on it, but I think it's not supposed to be mounted when I do so?

Or do I need to boot a Live CD and then mount the HDD?

Could someone please post the exact commands I would need to mount the HDD when booting through a Live CD.  I know how to mount a USB stick via the GUI, but don't know how to list the names of devices in order to mount the HDD.

Also, could you verify that I am doing this correctly?
My only goal is just to get those bad sectors out of use, I think they were caused by a power surge.

---

### Post by Pelham123 on 2008-09-08
Take a look here...

[http://ubuntuforums.org/showthread.php?t=841220](http://ubuntuforums.org/showthread.php?t=841220)

Then ignore all of this. Instead go out and buy a new HDD and re-install. Badblocks follow badblocks :p

---

### Post by idyllhands on 2008-09-08
That did it!  Thanks a bunch Pelham123

---

