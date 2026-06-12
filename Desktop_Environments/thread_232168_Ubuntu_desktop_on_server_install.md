---
title: "Ubuntu desktop on server install"
date: 2006-08-08
forum: Desktop Environments
---

### Post by veli on 2006-08-08
I'm going to install server 6.06 and after that I'll install the ubuntu-desktop. I don't want any programs like Open Office or Evolution, and many others like Games, so my question is: Are those programs getting installed by default with apt-get install ubuntu-desktop?

Or can I install only Gnome, and after that to add the necessary programs.

Thanks a lot,

---

### Post by Ramses de Norre on 2006-08-08
Yes, ubuntu-desktop installs those. But you can manually install an X server and gnome if you like.
It might be useful to look into the dependencies of ubuntu-base and ubuntu-minimal, I'm not sure what they install.

---

### Post by Titus A Duxass on 2006-08-08
Install the gnome desktop will bring lots of other packages with it including open office.

You may want to pick another WM and then install the packages you want. XCFE4 gives you a nice GUI without too much junk.  IceWM is even more minimalistic.

---

