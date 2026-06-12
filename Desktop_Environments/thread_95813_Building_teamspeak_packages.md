---
title: "Building teamspeak packages?"
date: 2005-11-27
forum: Desktop Environments
---

### Post by easy_target on 2005-11-27
Is it possible to build a deb of the tarball found at their website? (Just for my own personal use and organization within the package management system).

Thanks

---

### Post by Alibloke on 2005-11-27
I've had some luck with using alien for converting between rpm's and debs...it is meant to do tar.gz's too.

Try "alien --to-deb [filename].tar.gz" and it should work.

Then dpkg -i [filename].deb to install

---

### Post by aysiu on 2005-11-27
The TeamSpeak .tar.gz from the TeamSpeak website has an install shell script. Just extract the .tar.gz, double-click on the shell script, and choose to run it. It's that simple.

All the steps are in these screenshots (see attached).
Of course, they end up in the wrong order. Read them as 2nd, 4th, 1st and 3rd.

---

