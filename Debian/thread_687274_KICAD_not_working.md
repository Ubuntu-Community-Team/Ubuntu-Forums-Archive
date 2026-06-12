---
title: "KICAD not working?"
date: 2008-02-04
forum: Debian
---

### Post by regomodo on 2008-02-04
I just want to make sure. Can anybody get Kicad to work in Debian Testing?
Nothing happens, not even a segfault. It works fine in Debian stable though.

---

### Post by regomodo on 2008-02-04
Does nobody want to try? I just want to see if anybody else has this issue.

---

### Post by p_quarles on 2008-02-04
Just installed it to test it out, and it loaded fine for me.

---

### Post by regomodo on 2008-02-05
> **p_quarles said:**
> Just installed it to test it out, and it loaded fine for me.

in Debian Lenny right? When i downloaded the source and executed it from the terminal i noticed i got many xfce library errors. Are you using xfce by any chance?

---

### Post by p_quarles on 2008-02-05
Yes, Debian Lenny, but not Xfce (Fluxbox on top of KDM). Also, I installed the binary via APT, and didn't use the source. 

Before I installed it, I read a little about Kicad -- it doesn't depend on KDE, but it seems to respect it, so I wonder if it uses the crash handler? See if you get any different results running it with the "--nocrashhandler" argument. Without that option, many KDE apps will not give you any segfault output.

---

### Post by polmir on 2008-02-06
All deb packages of kicad:
[http://packages.debian.org/search?keywords=Kicad&searchon=names&suite=all&section=all&sourceid=mozilla-search]("http://packages.debian.org/search?keywords=Kicad&searchon=names&suite=all&section=all&sourceid=mozilla-search")
and try this link
[http://kicad.sourceforge.net/wiki/index.php/Main_Page]("http://kicad.sourceforge.net/wiki/index.php/Main_Page")
[http://ubuntuforums.org/showthread.php?t=262213]("http://ubuntuforums.org/showthread.php?t=262213")
[http://www.geda.seul.org/index.html]("http://www.geda.seul.org/index.html")

---

### Post by regomodo on 2008-02-12
> **p_quarles said:**
> Yes, Debian Lenny, but not Xfce (Fluxbox on top of KDM). Also, I installed the binary via APT, and didn't use the source. 

Before I installed it, I read a little about Kicad -- it doesn't depend on KDE, but it seems to respect it, so I wonder if it uses the crash handler? See if you get any different results running it with the "--nocrashhandler" argument. Without that option, many KDE apps will not give you any segfault output.

cheers. that worked. Don't know why it works in stable but not in testing.
Now that i've run that it appears to work each time i run kicad

---

