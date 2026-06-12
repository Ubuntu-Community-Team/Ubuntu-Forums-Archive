---
title: "KDesktop does not refresh"
date: 2005-07-14
forum: Desktop Environments
---

### Post by geearf on 2005-07-14
Hello,

just a little problem there, the desktop does not refresh.

Whenever i save a file from firefox, or even moving it from the konsole, the desktop does not change anything, even if i try "refresh the desktop", the only thing that works is creating a new folder, then the desktop refresh himself, and i can see the files that were not display before.

If anyone had an idea on this, (I suppose it's a kde specific problem not kubuntu).
Thanks

---

### Post by geearf on 2005-07-15
up

---

### Post by GeneralZod on 2005-07-15
I'm not to sure about what's happening behind the scenes, but it might be related to my pet bug:

[http://bugs.kde.org/show_bug.cgi?id=106394](http://bugs.kde.org/show_bug.cgi?id=106394)
[https://bugzilla.ubuntu.com/show_bug.cgi?id=11736](https://bugzilla.ubuntu.com/show_bug.cgi?id=11736)

In spite of the fact that I wrote it as being a Konqueror bug, it's actually a bug deep in the KDE internals that breaks the way it monitors changes to files - like the ones in the Desktop directory.  I've experienced it on two different distros now, but can't get *one single person* to confirm or deny it (including the developers!), which is really frustrating - especially as it would only take a few seconds!  ](*,)

---

### Post by geearf on 2005-07-15
Hello,
i've vote for both, now let's see what happens.

---

### Post by GeneralZod on 2005-07-15
[QUOTE=geearf]Hello,
i've vote for both, now let's see what happens.[/QUOTE]

Confirmation! Thanks very much :)

---

### Post by geearf on 2005-07-15
Well if we get a reply, i'll be thanking you :)

---

### Post by geearf on 2005-07-16
up in case anyone has the same problem / know something

---

### Post by geearf on 2005-07-18
up

---

### Post by geearf on 2005-07-20
:)

---

### Post by PhilippWollermann on 2005-07-21
Hi,

I have / had this problem too.. using Kubuntu + KDE 3.4.1. I'm not sure if it was fixed when I upgraded to kernel 2.6.13-rc3-mm1 with inotify compiled in. I'll check it and report back. :)

Philipp

---

### Post by geearf on 2005-07-21
Thanks for your report :)

I just want to add that i don't have this problem on the 3 kubuntu i have installed at work (32 and 64 bits) and i did'nt have this problem in my past installations in my own computer too (3 installations).

---

### Post by GeneralZod on 2005-07-21
[QUOTE=PhilippWollermann]Hi,

I have / had this problem too.. using Kubuntu + KDE 3.4.1. I'm not sure if it was fixed when I upgraded to kernel 2.6.13-rc3-mm1 with inotify compiled in. I'll check it and report back. :)

Philipp[/QUOTE]

If it's still not working, can you add your voice to either of the bug reports?

[http://bugs.kde.org/show_bug.cgi?id=106394](http://bugs.kde.org/show_bug.cgi?id=106394)
[https://bugzilla.ubuntu.com/show_bug.cgi?id=11736](https://bugzilla.ubuntu.com/show_bug.cgi?id=11736)

Cheers :)

---

### Post by geearf on 2005-07-26
up

---

### Post by geearf on 2005-07-30
new kde out, maybe it fixes this ?

I may try it tomorrow.

---

### Post by Freddy on 2005-07-30
Nope it don't, it's just appears to stop refreshing windows randomely and not often for me but it does happen and with Kubuntu using Kde 3.4.2 it does to. Haven't noticed it in any other distro I've tried in the last couple of month though, so I guess it a Kubuntu specific problem

/ Freddan

---

### Post by geearf on 2005-07-31
Hello,

it's not a specific Kubuntu problem, I had the same with Centos.

But the funny part is that I installed Kubuntu like 7 times, and only once I got this problem :)

---

### Post by geearf on 2005-08-01
True it does not fix the problem :(

---

### Post by geearf on 2005-08-01
And it seems it also did not help kplayer at all :(

---

