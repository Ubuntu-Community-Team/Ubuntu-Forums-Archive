---
title: "Does VMware Server need X?"
date: 2006-07-05
forum: Desktop Environments
---

### Post by Swad on 2006-07-05
The topic pretty much sums it up.  Do I need a GUI / X to install VMware Server on, or can I install it on a 6.06 server install that doesn't have X / a GUI?  Clearly there's some desirability in this in that you lose the extra overhread of X. The VMware Server Console would be used to remotely administer the server.

Thanks.

---

### Post by synthetic_fenix on 2006-07-08
I would be interested in this as well, I tried installing it and it complained about not having X installed but maybe there is a work around for this? I really don't need X on my file/game server But i want to run Windows Server 2003 in a WMWare server session on that box as well.

---

### Post by bartbes on 2006-07-08
You do need X, but you don't need Gnome, KDE, whatever.

---

### Post by Thund3rstruck on 2006-07-08
I need this functionality as well. I do not want a window manager (X) installed on my vmware server. How exactly do you go about installing X without installing gnome or KDE?

---

### Post by Swad on 2006-08-01
FYI (and sorry I never got back to this) -- you do NOT need to install X to run VMware Server.  I have been running VMware Server for several weeks now with just the server install and the necessary packages to support VMware Server (off the top of my head I can't recall these packages).  It really is fantastic in that you can just use the console / ssh / mui to manage the server and you can save a lot of resources by never touching X or having it running.

---

### Post by doogy2004 on 2006-10-30
What are the packages?

---

### Post by civic_si on 2006-11-28
The machine does not need a Window manager like Gnome or KDE. you can use wget to download the packages that you need to install the server. there is also a web interface that you can download and install vmware-mui-1.0.1-2996.tar.gz this will give you an apache based website to login too and see the servers memory and processor usage. all of the packages needed are free which makes it very nice.
[http://itgeek.squarespace.com/journa...erver-610.html](http://itgeek.squarespace.com/journa...erver-610.html)

use this link it gives good instructions to get it running on 6.10 server which has no GUI. ot you could probably just use the existing installation you have and just change the run level of the box so the GUI is there but it does not start and take up CPU and Memory. the post is kind of late but better that never. I guess.:-|

---

### Post by doogy2004 on 2006-11-28
here is a link to the required packages to run vmware server

[http://www.ubuntuforums.org/showpost.php?p=1711663&postcount=3](http://www.ubuntuforums.org/showpost.php?p=1711663&postcount=3)

---

