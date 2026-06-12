---
title: "HELP ME to set up a virtual printer!"
date: 2005-12-11
forum: General Help
---

### Post by sourc3 on 2005-12-11
Hello everyone, I need help!
I'm trying to set up a virtual printer, mainly to convert documents into pdf format. What's the fastest and EASIEST way of doing this? Can you help me? Thanks in advance! ;)

---

### Post by tomchuk on 2005-12-11
Install cups-pdf. If you'd like to use it from Windows machines, install samba as well. Configure samba to share your cups printers, and in the cups-pdf config file, set the output directory to a shared samba directory. Clients can then print to the pdf printer and then grab their pdf's from the share.

---

### Post by sourc3 on 2005-12-11
Sorry but I can't get it done. I've installed cups-pdf and installed the "virtual" pdf printer, but when I issue the print command (for example from evince) the printer goes into pause mode and I can't get it working! What I did wrong?

---

