---
title: "How do I get rid of compiz fusion?"
date: 2007-06-24
forum: Desktop Effects &amp; Customization
---

### Post by 71CH on 2007-06-24
Can somebody tell me how to completely uninstall compiz fusion and get my comp back to the way it was.  Thanks.

---

### Post by llamakc on 2007-06-24
ALT+F2 for the run dialog. Type in:

metacity --replace

Open Synaptic and remove the packages that you installed.

---

### Post by Happy_Man on 2007-06-24
GASP!!!! WHY???? WHY???? WHYYY??????? *tears*

I guess (if you used Trevino's repos) you could just remove all the compiz packages thru Synaptic, delete Trevino's repos so that they aren't updated, and reinstall the Feisty compiz....

---

### Post by cwood06 on 2007-06-24
You can do a apt-get remove compiz compiz-fusion-* that should get rid of it then delete the sorces either from gui or the source.list

then if you want the old one you can use do a sud0 apt-get install compiz

also check out the ubuntuguide.org wiki gives great how-to's they often work for me.

---

