---
title: "How to pass on my change of xorg.conf to a Live CD"
date: 2009-06-12
forum: Desktop Environments
---

### Post by chang5562 on 2009-06-12
How can I pass on my change of xorg.conf to a Live CD (or Live USB) platform?

I tried to disable the user to use the Ctrl-Alt-F1~12 shortcut keys which access the tty.  I configured this on a desktop (or a laptop) and it worked.  However, this change would not pass onto a Live CD version.  The change, 
Section "ServerFlags"
Option "DontVTSwitch" "true"
EndSection

was added to /etc/X11/xorg.xonf; but this was not transferred into Live CD filesystem. The xorg.conf is more local specific configuration.  How can I create a Live CD with the same configuration?

---

### Post by cariboo on 2009-06-12
You can't add anything to an iso file, but you can create a new iso using something like [Remastersys]("http://www.geekconnection.org/remastersys/remastersystool.html").

---

### Post by chang5562 on 2009-06-12
I might mislead u what I intended to to.  I knew I could not add to iso file.  I was using the remastersys to create the iso.  However, whatever I changed to the xorg.conf file would not be included into the iso, therefore, the disable of Ctrl+Atl+F[1~12] was not there in Live CD.  It was the same as that of the menu.lst of /boot/grub/. 

So I am wondering whether there is another way to keep the Ctrl+Alt+F[1~12] out when using the Live CD.

---

