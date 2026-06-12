---
title: "Make one users files / folders writable by another?"
date: 2009-05-10
forum: General Help
---

### Post by ownaginatious on 2009-05-10
I'm currently using the TorrentFlux bittorrent client on my file server, and I'm having problems where everything it downloads is owned by the user 'data-www', which I understand is the apache user.

So my question is, is there a way to make anything created by the data-www user completely readable and writable by my account? I can change the permissions using chown to allow myself read and write permissions, but I keep having to do it every time new files are added.

Thanks,

Dillon

---

### Post by mb_webguy on 2009-05-10
The data-www user probably belongs to the data-www group, and the files created by that account are probably readable/writable by that group.  So you could just add your user account to that group in order to gain access to those files.

---

### Post by ownaginatious on 2009-05-10
> **mb_webguy said:**
> The data-www user probably belongs to the data-www group, and the files created by that account are probably readable/writable by that group.  So you could just add your user account to that group in order to gain access to those files.

I knew it was something simple like that. Thanks :)

---

