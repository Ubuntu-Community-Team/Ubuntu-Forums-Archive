---
title: "Expand .sitx files from Stuffit"
date: 2005-12-22
forum: General Help
---

### Post by dj_flx on 2005-12-22
Is there any crafty workaround that will let me expand a .sitx file in Linux period?

The *nix unstuff at the stuffit.com site doesn't recognize it. :(

---

### Post by altonbr on 2007-05-10
Apparently File Roller supports extracting .sit (StuffIT) archives: [http://fileroller.sourceforge.net/features.html](http://fileroller.sourceforge.net/features.html)

But the version I have in Feisty doesn't seem to support it (2.18.1)

---

### Post by BetaMaster on 2007-05-13
altonbr - he's looking for something to unstuff an sitx file, which is Aladdin's newer SIT format (i.e. not the same as .sit)
I'd like a way to unstuff an sitx file too, I need a way to do it.

Thanks as well!

---

### Post by jjalocha on 2007-05-23
I am trying ot open a '.sit' file, the (older?) stuffit compressed file, and Xarchiver 0.4.6 under Xubuntu Feisty doesn't recognize it.

Any help?

---

### Post by onbongos on 2007-05-24
you can install [this bit of idiocy]("http://www.stuffit.com/unix/index.html") but the best thing is to expand on mac/windows and immediately recompress in a nonencrypted format like zip or tgz

---

### Post by jjalocha on 2007-05-25
Thank you! I will take a look at it, but I think, I'll just ask the senders of these files to use a more friendly format. I think this is one of these cases where a propietary format CAN and should completely be avoided.

---

### Post by rubberglove on 2007-11-05
> **onbongos said:**
> you can install [this bit of idiocy]("http://www.stuffit.com/unix/index.html") but the best thing is to expand on mac/windows and immediately recompress in a nonencrypted format like zip or tgz

that idiocy is even worse than you think:

```
$ ./unstuff --formats
sit, cpt, zip, arc, arj, lha, rar, gz, compress, uu, hqx, btoa, mime, tar, bin, sitseg, sitsegN, pf, sit5, bz2, apple

```

That is, it doesn't actually support sitx files! Those are only supported on OSX/Windows.

---

