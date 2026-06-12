---
title: "Help with Java in Breezy Badger"
date: 2005-10-14
forum: Desktop Environments
---

### Post by brent420 on 2005-10-14
I'm not a very experienced linux user but i'm having problems with the system recognizing that i've installed jre1.5.0_05.  I finally just fixed the mozilla plugins but azureus doesn't work properly.  Any help?

---

### Post by Curlydave on 2005-10-14
Dont' use that jre thing. Just go to a java page in FF and now it installs automatically like it does in WIndows.

---

### Post by rumli on 2005-10-14
[QUOTE=brent420]...i'm having problems with the system recognizing that i've installed jre1.5.0_05...[/QUOTE]

Try the following:

sudo update-alternatives --config java

Then select sun jre as the default.

---

### Post by nix4me on 2005-10-14
That worked for me.  I was able to use Secureftp after doing that.

---

