---
title: "Problem Installing Unreal Tournament 2004 Demo"
date: 2007-05-07
forum: Gaming &amp; Leisure
---

### Post by Ultracoder05 on 2007-05-07
Hey. I'm trying to install Unreal Tournament 2004 (the demo) on my computer. However, when I try to extract the .run.gz file, it says there is an unexpected end of file name. Can someone help?

---

### Post by DoktorSeven on 2007-05-07
I got that a lot; it seems very few sites actually have a complete and working installer for UT2k4 demo for LInux for some bizarre reason.  

I think the files on the Gentoo mirrors ([http://www.gentoo.org/main/en/mirrors.xml](http://www.gentoo.org/main/en/mirrors.xml)) are correct, so go try one (it's under distfiles/, and isn't just for Gentoo; it should be named something like ut2004-lnx-demo3334.run).

---

### Post by menelmacar on 2007-05-26
> **DoktorSeven said:**
> I got that a lot; it seems very few sites actually have a complete and working installer for UT2k4 demo for LInux for some bizarre reason.  

I think the files on the Gentoo mirrors ([http://www.gentoo.org/main/en/mirrors.xml](http://www.gentoo.org/main/en/mirrors.xml)) are correct, so go try one (it's under distfiles/, and isn't just for Gentoo; it should be named something like ut2004-lnx-demo3334.run).
That worked for me. Thanks.
It's kind of ironic considering I just came to Ubuntu after using Gentoo since 2004.

---

### Post by ipreferpi on 2007-06-11
I had a similar problem, so i downloaded a new version of the file, but I have no idea how to install it. Any help would be wonderful.

---

### Post by Cappy on 2007-06-12
It will be something like
```

cd ~/Desktop
sudo chmod +x ut2004-lnx-demo3334.run
sudo sh ut2004-lnx-demo3334.run

```

This assumes that it is on your Desktop and the file name is "ut2004-lnx-demo3334.run"

---

