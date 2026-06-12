---
title: "Gnome Network Manager slows startup of Gnome Toolbar and other apps"
date: 2007-05-25
forum: Desktop Environments
---

### Post by yusufk on 2007-05-25
Hi,

I noticed that everytime I boot up my laptop at work it hangs after the gnome login. It usually gets stuck right before the icons appear on the gnome toolbars. 

Even after the icons appear, everything takes ages to load, including a shell window.

At 1st I thought that it had something to do with the fact that I use dual monitors at work. Then I noticed that when I click on the network manager and on wired connection, it disconnects and reconnects me to the lan and immediately after that everything seems to respond normally.

Anybody else experience this?

---

### Post by 8oluf7 on 2007-05-27
I had something similar, caused by something I'd set in Dapper to mount the shared files on a Windows machine at startup not working with Feisty. The network manager made several attempts to find a location that evidently  was no longer specified correctly. It may even have been tripping over a space in the location name. 

[INDENT][http://ubuntuforums.org/showthread.php?t=414973](http://ubuntuforums.org/showthread.php?t=414973)[/INDENT]

Anyway - I completely removed smbfs and samba (to purge the configuration files) restarted and re-installed them. Crude - but it worked.

---

