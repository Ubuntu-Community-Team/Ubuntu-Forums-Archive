---
title: "Restart in windows button"
date: 2007-08-10
forum: Desktop Environments
---

### Post by aquavitae on 2007-08-10
I remember a couple of years ago seeing, in Suse, a logout option "Restart in Windows". Does anyone know how to add such an option to ubuntu?  Does anyone know how to customise the entire logout window (i.e. the one with the restart, shutdown, etc buttons)?  I have no problem with changing code, but I don't know what code to change.

---

### Post by Chris S. on 2007-08-10
From what I can tell, this can not really be done with the GRUB bootloader, but there are tricks you can try.

Check out [bootnext]("http://www.dcheng.members.sonic.net/friends/jspaar/pub/bootnext/") and more specifically the last few posts of [this thread]("http://ubuntuforums.org/showthread.php?t=394967").  The basic idea is that you can use bootnext to auto boot into an OS of your choosing from Ubuntu, like you want.  However, the default OS that GRUB boots into otherwise will be the last OS you booted into manually (i.e. from the GRUB boot list).  It shouldn't be an issue if you always start up into Ubuntu, and only boot into Windows using bootnext.  See the thread for more details.

---

### Post by aquavitae on 2007-08-12
Thanks, that sorts out part of it, but I'd still like to know how to change the logout screen (I'm using KDE), if its possible, without changing the source.  Any ideas?

---

### Post by Chris S. on 2007-08-12
That I don't know, but KDE is a good place to be if it is possible.  Glad to help, even if only a little.

---

