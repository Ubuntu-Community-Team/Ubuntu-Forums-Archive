---
title: "synaptic not in desktop"
date: 2008-01-10
forum: Desktop Effects &amp; Customization
---

### Post by metaphorz on 2008-01-10
I just installed ubuntu desktop over ubuntu server (both version 7.10),
and noticed that even though the Synaptic Package Manager is installed
(under /usr/sbin/synaptic, /usr/share/synaptic), the Manager does not
show in SYSTEM->ADMINISTRATION. All other aspects of the desktop
and system seem to be OK, but have not yet checked in detail.

1) Any ideas why a fresh install of Ubuntu 7.10 would leave this out?

2) Can I correct for it by putting it in manually under System->Administration ?

Thanks.

---

### Post by rune0077 on 2008-01-10
Try right-clicking the menu part and select Edit Menus. This should give you a "tree-like" view of the menu structure. At the very bottom you'll find System>Administration - Synaptic should be available here if you just check its box. It's odd though, because it should be there by default.

---

### Post by metaphorz on 2008-01-10
I am in Edit menus as suggested, and the items that I
need (such as Synaptic) are listed but they are in italics, so when I try to
click on "Show" next to them, this change doesn't
stick (my check mark disappears after a few seconds).

---

### Post by rune0077 on 2008-01-10
Okay, then you probably don't have Synaptic installed. Try this in terminal:

```
sudo synaptic
```

See if it'll complain or let you run it.

---

### Post by metaphorz on 2008-01-10
It runs fine at the shell.

When I run it at the shell (sudo synaptic), I scroll
down to "synaptic", and it shows that
I have 0.60ubuntu5 installed with a size of 6074KB.

So, it is installed,and I can run it via the shell,
 but it is not showing up in Gnome for some reason.

---

### Post by metaphorz on 2008-01-10
Here is a follow-on:

 I right-clicked on the italicized "Synaptic Package Manager" and
a "Launcher Properties" window pops up. In this window, everything
is set correctly:

 Type: Application
 Name: Synaptic Package Manager
 Command: gksu /usr/sbin/synaptic
 Comment: install, remove and upgrade software


When I get a terminal window, and enter "gksu /usr/sbin/synaptic"
it works fine.

---

### Post by metaphorz on 2008-01-10
I found the problem after digging, but there is a minor nagging
question:

On another Ubuntu machine, I noticed after running users-admin
that on that machine, my username had "Administer the System"
checked under User Properties. However, on the new Ubuntu machine, that
box was unchecked for some reason. So, I checked that box,
relogged into the system, and am now able to see all of the
System->Administrator items including Synaptic Package 
Manager. This must be the reason why it was previously
italicized.

However, I then encountered a second issue: My username was not in
the "sudoers" list and because of this I was not able to launch Synaptic
Package Manager from Gnome.  So I put it there by using visudo and adding
"username ALL =  ALL (ALL)" right after the root user privilege.

Now, here is the odd thing: In the other Ubuntu computer, I do
NOT have this line in the sudoers file (the only line in there is the
one for root), and I am able to see and run Package manager, etc.

Anyway, now that I have manually added my username in /etc/sudoers
using visudo, everything is back to normal or so it would seem. I am
not sure what is going on with sudoers, but some more research might
shed light.

---

### Post by rune0077 on 2008-01-10
Great that it's working. I'm guessing that it may have been a Permission problem (maybe Synaptic was set to Administrator-only access). This would make sense on a server system, wouldn't it?

---

