---
title: "Cannot right-click and 'paste' anything in PCManFM"
date: 2013-07-01
forum: Desktop Environments
---

### Post by M_Mynaardt on 2013-07-01
Hi there!

A bit of an odd one happening for me lately with PCManFM.  If I select a file or directory, then right click and choose either 'cut' or 'copy' all looks well.  But if I go to another directory and then right click; 'paste' is always greyed out and won't work.

At the same time, if I drag files or directory to another directory showing on the same tab, that moves the files just fine.  And the "mv" and "cp" commands move just fine.

It's a bit of a bother.  If, for some reason, I want to move or copy files from, say "~/documents/receipts" to "/media/buddy/32gig" I can't drag and drop into different tabs in the same window, although I can drag and drop between different windows of PCManFM.

Does anyone know why the right-click->paste option would be disabled in PCManFM?  And how to enable it?  I find it's handy to have one window of PCMan with multiple tabs when I want to reorganize my files sometimes, so this paste option being disabled is a bit of a nuisance.

I *think* this might have started with Lubuntu 13.04.  I'm not 100% sure, though.  I've got Lubuntu installed on two laptops: a Toshiba Satellite A100 (32 bit Lubuntu) and a much newer Asus X55u (64 bit Lubuntu).  And in both, the right-click-paste option is dsabled in PCManFM.

Anyway...  If anyone could tell me how to enable that handy little paste thingy, it would be ever so nice!

Thanks in advance!
:cool:

---

### Post by Dennis N on 2013-07-01
Lubuntu 13.04 here. The right-click and copy/paste are working normally on my system, so it is not PCManFM having the function disabled in Lubuntu 13.04.

Here is another similar report that offers some information for you:

[http://forum.lxde.org/viewtopic.php?f=22&t=36214](http://forum.lxde.org/viewtopic.php?f=22&t=36214)

---

### Post by M_Mynaardt on 2013-07-01
> **Dennis N said:**
> Lubuntu 13.04 here. The right-click and copy/paste are working normally on my system, so it is not PCManFM having the function disabled in Lubuntu 13.04.

Here is another similar report that offers some information for you:

[http://forum.lxde.org/viewtopic.php?f=22&t=36214](http://forum.lxde.org/viewtopic.php?f=22&t=36214)

Well, that was an easy fix!  No idea why Parcellite was causing PCManFM to act like that.  :confused:  

I replaced Parcellite with Clipit and now it's working properly.

Thanks for that; I never would've connected a PCManFM problem to a clipboard manager like that!
8-)

---

