---
title: "Gnome Update Notifier"
date: 2009-05-12
forum: General Help
---

### Post by Chris_Smith on 2009-05-12
Hi Guys,

I have been experimenting with the "checkinstall" utility that can build Debian packages from compiled source code, and although checkinstall works perfectly, and is a very useful tool, I have run into a problem when using it on a system that is running the Gnome update manager/notifier..

 I am using Ubuntu 8.04 Hardy Heron with the xfce4 desktop, and as I do not have an Internet connection, I have to install files either by down loading them onto a pen drive at another location, or by using Ubuntu installation CDs and DVDs. When I first installed Ubuntu Hardy, I used the "apt-cdrom add" command to catalogue my installation DVD, which makes installing packages much easier, as all the dependencies are installed automatically. I have just compiled the ffmpeg trans-coding utility using the latest stable source code, and included support for a few more external codec libraries such as libmp3lame which is not supported by the 3:0.cvs20070307-5ubuntu7 version of ffmpeg on the installation disk. After compiling the the v0.5 source code, I then used "checkinstall" to build the new Debian package, which is called "ffmpeg_20090510-0.5-1.deb. After installing the package I found that the Gnome update notification icon had appeared in the system tray informing me that I had one new update pending. The update manager seems to think that the older cvs version on the DVD is better than the newly compiled one, and wants to replace it. Does anyone know how to resolve this problem without uninstalling or disabling the update notifier?
-------------
Best regards,
CS

---

### Post by Brandon Williams on 2009-05-12
I think that the update notifier will stop bothering you if you flag your version for hold. Try 'sudo aptitude hold ffmpeg'. Hopefully, this will be enough.

If not, then run checkinstall again and specify a different version number for your package, one that will be interpreted as newer than the official ubuntu one. This may be tough to figure out, given the strange version number of the official package. You could try 3:0.cvs20090510-0ubuntu1 to start with, and if that doesn't work, then investigate debian version numbering a bit further to come up with another suggestion.

---

### Post by Chris_Smith on 2009-05-19
Thanks for the reply Brandon, I have contacted the Checkinstall developers and their reply was as follows:

I believe maybe playing with the version, release and epoch numbers in the Debian control file (Use the --review-control flag when running checkinstall) should help. I'll forward your message to the checkinstall mailing list which has some Debian packaging gurus, maybe they can give you some tips.

---

