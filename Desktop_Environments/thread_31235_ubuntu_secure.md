---
title: "ubuntu secure?"
date: 2005-05-02
forum: Desktop Environments
---

### Post by kestasjk on 2005-05-02
Hi, I just ditched gentoo after portage screwed my system up *again* and I'm really liking ubuntu, seems like a very solid OS.

Anyway the problem is that I'm not sure whether all of the software on this system is patched and secure. I've got a few universal packages installed, and I'm not sure whether they get updated security wise. Also I don't see a linux kernel package, which means that any kernel vulnerabilities will go unfixed for 6 months.
I know for a fact that there have been firefox vulnerabilities since 1.0.2, yet despite this installation being apparently up to date firefox 1.0.2 is here.

Can anyone help me with my concerns? Thanks,

---

### Post by tread on 2005-05-02
You need to visit ubuntu-backports for that. Heres a link that might be useful:

[Ubuntu backports](http://backports.ubuntuforums.org/)

---

### Post by shakin on 2005-05-02
1) Universe packages aren't guaranteed to be updated, which is why it's not enabled by default. Read [http://www.ubuntulinux.org/ubuntu/components/document_view](http://www.ubuntulinux.org/ubuntu/components/document_view)

2) While the kernel will not be upgraded, it will get security patches backported. Check out the linux-386, linux-686 and linux-686-smp packages.

3) Add the Hoary backport repositories to your /etc/apt/sources.list file (or through Synaptic). Firefox 1.0.3 is there. The info is at [http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/)

---

### Post by nocturn on 2005-05-03
[QUOTE=kestasjk]
I know for a fact that there have been firefox vulnerabilities since 1.0.2, yet despite this installation being apparently up to date firefox 1.0.2 is here.

Can anyone help me with my concerns? Thanks,[/QUOTE]

FireFox is a bit of a soar issue lately and I hope it will get better in the future.
That said, Hoary will not get FF 1.0.3, instead the fixes are applied to 1.0.2.
So far, a number of 1.0.3 fixes are already in, but the favicons/javascript vuln remains (should be fixed this week).

---

### Post by A-star on 2005-05-03
But you can get the latest version of firefox from the backports repository.

---

### Post by az on 2005-05-03
linux-image, not kernel image.  Yes you will get the latest kernel secutiry updates!

---

### Post by kestasjk on 2005-05-05
Thanks for the help, I'll try to keep to main packages as much as possible. But is even the main distribution set kept up to date security wise? Of the 800 or so packages I've got installed I haven't had to update any for days :-|

---

### Post by Fab on 2005-05-05
[QUOTE=kestasjk]Thanks for the help, I'll try to keep to main packages as much as possible. But is even the main distribution set kept up to date security wise? Of the 800 or so packages I've got installed I haven't had to update any for days :-|[/QUOTE]
 security fixes are incorporated into main by the ubuntu developers, as long as they dont break stuff i think

---

