---
title: "Networking to Windows in Xfce?"
date: 2007-05-05
forum: Desktop Environments
---

### Post by wog on 2007-05-05
Is there some sort of trick to accessing networks with Xfce? In Gnome, all I had to do was get into the menu to look for a server, and it found my Windows machines just fine. With Xfce, even with the installation of Samba, I can't figure out how to access the Windows machines.

---

### Post by aysiu on 2007-05-05
Try [this](http://ubuntuforums.org/showpost.php?p=2576716&postcount=20).

---

### Post by afoglia on 2007-05-06
Try pyNeighborhood (available in the universe repository).  I haven't used it myself, but it seems to be what people in Xfce are using.

[http://pyneighborhood.sourceforge.net/index.html]("http://pyneighborhood.sourceforge.net/index.html")
[http://grumpymole.blogspot.com/2006/11/xubuntu-browsing-samba-shares-with.html]("http://grumpymole.blogspot.com/2006/11/xubuntu-browsing-samba-shares-with.html"), instructions on how to configure it, if you have any problems (ignore the first section on compilation)

---

### Post by asipi on 2007-05-07
try smb4k, I am satisfied with it in also company network but take in mind that all samba related tools has some problems with crossnetwork browsing of windows shares. it will only bother you on a huge company network with several subnets.

smb4k however is a kde apps but I also use it under xfce without any problem.

---

### Post by dolphin_oracle on 2007-05-07
What you want is fuse - check out this Howto.  it will allow you to browse your network not only in Thunar but in any file dialog.

[http://ubuntuforums.org/showthread.php?t=304131&highlight=xubuntu](http://ubuntuforums.org/showthread.php?t=304131&highlight=xubuntu)

---

### Post by DJiNN on 2007-05-07
> **dolphin_oracle said:**
> What you want is fuse - check out this Howto.  it will allow you to browse your network not only in Thunar but in any file dialog.

[http://ubuntuforums.org/showthread.php?t=304131&highlight=xubuntu](http://ubuntuforums.org/showthread.php?t=304131&highlight=xubuntu)

I'll second that. I've got both Xubuntu Feisty 32 bit (running on 3 machines) and the 64 bit version on my laptop. It's always veen a struggle getting Thunar to do what Nautilus (Gnome) does quite naturally....... until i followed that how-to by Tazix. Now i've got all my Xubuntu machines talking really well, and it's so straightforward it's incredible. 

It makes Xubuntu the distro that it should be.  

Try it, you won't be disappointed. :)

DJiNN

---

