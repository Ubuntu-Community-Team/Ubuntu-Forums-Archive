---
title: "Applications keep disappearing!"
date: 2009-05-11
forum: General Help
---

### Post by ukblacknight on 2009-05-11
I did a fresh install of 9.04 when it came out, on 64bit, ext4.

There is an extremely annoying bug - applications keep disappearing!  It's noticeably the same applications too:
[LIST]
[*]Opera
[*]Virtual Box
[*]dropbox
[/LIST]

I have to re-install them once a week.  Using the which command returns nothing, and locate doesn't return any entries for /usr/bin etc etc.

It doesn't seem to of happened with any other applications, that I've noticed.  Could this be ext4 related?  Anyone else experiencing this?

---

### Post by HavocXphere on 2009-05-11
Those are all the applications that you installed manually, right?

There was a thread today/yesterday about a guy who said that the janitor app removes all apps that were installed by hand.

Maybe its that...

---

### Post by ukblacknight on 2009-05-11
Hmm it could be something to do with that actually.  Yes, the applications were installed by hand (downloaded deb and installed through gdebi).

I have, however just added the VirtualBox repo and installed it via that, so hopefully that shouldn't happen again.  I *think* there is a repo for dropbox so I'll get on that too.

I just checked the Janitor and dropbox plus opera are in there, which were installed manually.  I thought the Janitor removed the .deb files that were used for installation, found in /tmp?  Any idea why it would remove the binary from /usr/bin?

I'll avoid the Janitor for a while, see how my experience plays out.  Cheers for pointing that out :)

I'm not entirely convinced about the whole Janitor thing anyway, I think it's something that should be handled discreetly rather than have a Windows style "clean up" method.

---

### Post by Zoowey on 2009-05-11
> **ukblacknight said:**
> Hmm it could be something to do with that actually.  Yes, the applications were installed by hand (downloaded deb and installed through gdebi).

I have, however just added the VirtualBox repo and installed it via that, so hopefully that shouldn't happen again.  I *think* there is a repo for dropbox so I'll get on that too.

I just checked the Janitor and dropbox plus opera are in there, which were installed manually.  I thought the Janitor removed the .deb files that were used for installation, found in /tmp?  Any idea why it would remove the binary from /usr/bin?

I'll avoid the Janitor for a while, see how my experience plays out.  Cheers for pointing that out :)

I'm not entirely convinced about the whole Janitor thing anyway, I think it's something that should be handled discreetly rather than have a Windows style "clean up" method.

If you want to clean your computer without uninstalling things you need download Ubuntu Tweak. It is one of the best utilities for Ubuntu for managing and keeping Ubuntu clean.

[http://www.getdeb.net/release/4325](http://www.getdeb.net/release/4325)

---

