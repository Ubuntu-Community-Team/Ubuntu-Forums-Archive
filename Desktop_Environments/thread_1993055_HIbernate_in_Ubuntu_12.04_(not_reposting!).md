---
title: "HIbernate in Ubuntu 12.04 (not reposting!)"
date: 2012-06-01
forum: Desktop Environments
---

### Post by zayid on 2012-06-01
Hello, i installed Ubuntu 12.04 on an 80GB partition with 4.2GB swap on a Speedstar laptop with 500GB HDD, 4GB RAM, Intel i7-620M 2.66GHz dualcore processor. So after going through posts on this forum,
i 1st ran ```
sudo apt-get install hibernate
``` then 
i ran ```
sudo pm-hibernate
``` then the system shut down and when i restarted, all my open applications were still open - meaning my system can hibernate.
i ran ```
sudo nano /etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla
``` and and changed the [HTML][Disable hibernate by default]
   Identity=unix-user:*
   Action=org.freedesktop.upower.hibernate
   ResultActive=no[/HTML] with [HTML][Re-enable hibernate by default] Identity=unix-user:* Action=org.freedesktop.upower.hibernate ResultActive=yes[/HTML].
I also ran ```
sudo gedit /var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla
``` and changed the [HTML][Disable hibernate by default]
  Identity=unix-user:*
  Action=org.freedesktop.upower.hibernate
  ResultActive=no[/HTML] at the bottom with [HTML][Re-enable hibernate]
  Identity=unix-user:*
  Action=org.freedesktop.upower.hibernate
  ResultActive=yes[/HTML] 
Can i add that it used to hibernate without problems on Ubuntu 11.10 but my power options still has no hibernate:( 
I need help thanks a lot

---

