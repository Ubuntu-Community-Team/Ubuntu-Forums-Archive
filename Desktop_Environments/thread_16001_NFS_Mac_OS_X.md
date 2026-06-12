---
title: "NFS Mac OS X"
date: 2005-02-18
forum: Desktop Environments
---

### Post by nachobel on 2005-02-18
is anyone here using ubuntu to export an NFS share to a mac os x computer, complete with write access?  If so, how are you doing it?  I'm getting error -50 when I try to write to the NFS share in my mac os x box. my /etc/exports includes rw, async, and insecure.  I can read from the share fine, I can even make new folders, I just can't write files to the share.

I'm stumped.

---

### Post by Tias on 2005-04-14
[QUOTE=nachobel]is anyone here using ubuntu to export an NFS share to a mac os x computer, complete with write access?  If so, how are you doing it?  I'm getting error -50 when I try to write to the NFS share in my mac os x box. my /etc/exports includes rw, async, and insecure.  I can read from the share fine, I can even make new folders, I just can't write files to the share.

I'm stumped.[/QUOTE]
 Hello :)-

You have probably got your ansver from some other source, but I'll post anyways. The problems proably lies with different uid on the OS X machine vs. the GNU/Linux computer, and I'm willing to bet that if you either change the uid on the OS X machine to 1000 or 500 on the GNU/Linux machine it will work fine.

I jused to have a properly working NFS-server on my box running Gentoo, but since I was so god damned clever that I decided it needed a cleenup and new distro I now have no working NFS :/. Oh well, hope I get it fixed tonight!

---

