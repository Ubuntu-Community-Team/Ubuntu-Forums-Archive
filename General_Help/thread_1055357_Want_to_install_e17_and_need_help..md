---
title: "Want to install e17 and need help."
date: 2009-01-30
forum: General Help
---

### Post by Universal344 on 2009-01-30
I found this on the forums:
[http://ubuntuforums.org/showthread.php?t=916690](http://ubuntuforums.org/showthread.php?t=916690)

However, I need some clarification.  The second post says that the etk package still needs cvs on building configuration.  I really don't know what any of this means.  If I run 'sudo apt-get install cvs' and then run through the howto will e17 install correctly?

I am installing on a completely new up to date Ubuntu 8.10 install.

Thanks for all your help.

---

### Post by Tux Aubrey on 2009-01-30
> **Universal344 said:**
> I found this on the forums:
[http://ubuntuforums.org/showthread.php?t=916690](http://ubuntuforums.org/showthread.php?t=916690)

However, I need some clarification.  The second post says that the etk package still needs cvs on building configuration.  I really don't know what any of this means.  If I run 'sudo apt-get install cvs' and then run through the howto will e17 install correctly?

I am installing on a completely new up to date Ubuntu 8.10 install.

Thanks for all your help.

"sudo apt-get install cvs" is part of the how-to (see the step before "sudo apt-get install e17-svn" ).  It actually doesn't matter when you run that command - cvs is older version of the version control system.  Although the e17 developers now use svn, that one package still needs cvs.

Just be aware that when you do run "sudo apt-get install e17-svn" there will be a long download and compile process.  Later, when and if you decide to update, you run "sudo easy_e17.sh -u" and just the packages that need updating will be downloaded and compiled.

Good luck!

e17 is a wonderful DE and right now the builds are very solid.  Rui's e17_svn script takes a lot of the potential hassle out of it.

---

### Post by Universal344 on 2009-01-30
Thank you for your response.  So if I just follow the howto step by step I should be fine?

---

### Post by Tux Aubrey on 2009-01-31
Sure.  Ask here or at CafeLinux if you strike a problem.

---

