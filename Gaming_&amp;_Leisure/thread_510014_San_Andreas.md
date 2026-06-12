---
title: "San Andreas"
date: 2007-07-26
forum: Gaming &amp; Leisure
---

### Post by Xenophoribic on 2007-07-26
I'm trying to get San Andreas installed, but every time I get into the Install Shield loading bar, it ends with:

> err:seh:setup_exception stack overflow 12 bytes in thread 0010 eip 7bc5042c esp 00240ff4 stack 0x241000-0x350000

---

### Post by Brynster on 2007-07-26
I assume that you are using either wine

If you check on [http://appdb.winehq.org/appview.php?iVersionId=3780](http://appdb.winehq.org/appview.php?iVersionId=3780)

There are all the instructions/tweaks you'll do to make San Andreas work

---

### Post by Xenophoribic on 2007-07-26
Unfortunately, that doesn't help at all. I can't find anything that helps to resolve the error I get when trying to install.

And yes, I am using Wine, forgot to mention it in my original post.

---

### Post by Xenophoribic on 2007-07-28
Bump

---

### Post by cogadh on 2007-07-28
Have you installed the [InstallShield bugfix]("http://support.installshield.com/kb/files/Q108322/IkernelUpdate.exe") in Wine? That may fix the problem.

Also, what version of Wine are you using?

---

### Post by Xenophoribic on 2007-07-28
I was unaware there was such a fix, hopefully that helps.

I'm running  0.9.41

Edit: Just tried running the bugfix, but it also gave me a stack overflow error.

---

### Post by cogadh on 2007-07-28
Have you ever installed anything else in Wine? It sounds like there might be something wrong with either your Wine installation or your Wine "fake Windows" directory.

---

### Post by Xenophoribic on 2007-07-29
I installed WoW with no problems. I also have no problem running it.

---

### Post by Xenophoribic on 2007-07-29
Bump.

Also, I was able to install Counter-Strike: Source just a little while ago with no problems.

---

