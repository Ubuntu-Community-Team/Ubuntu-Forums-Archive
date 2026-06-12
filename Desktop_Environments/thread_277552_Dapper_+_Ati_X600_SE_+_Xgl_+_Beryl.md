---
title: "Dapper + Ati X600 SE + Xgl + Beryl"
date: 2006-10-14
forum: Desktop Environments
---

### Post by acid_burn on 2006-10-14
hi all!
i've installed xgl and beryl on a toshiba satellite m50 with ati x600 SE running ubuntu dapper following these instructions: [http://wiki.cchtml.com/index.php/Xgl-Compiz-Dapper](http://wiki.cchtml.com/index.php/Xgl-Compiz-Dapper) (from ubuntuguide.org). it runs fine! it's fantastic!

now, if i modify /etc/X11/gdm/gdm.conf-custom adding:

[servers]
1=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl -fullscreen -ac -accel glx:pbuffer -accel xv:pbuffer
flexible=true

and restart gdm, it runs very slow, and beryl won't start (if i select beryl instead of metacity from beryl manager, it revert to metacity).

how can i run xgl from gdm instead of using the dedicated session (/usr/bin/startxgl.sh & /usr/share/xsessions/xgl.desktop from the guide)?
using the dedicated session, i cannot halt or reboot the system, i have to logout and then halt/reboot the system from gdm menù!!!

thanks in advance!!!

---

### Post by acid_burn on 2006-10-15
little UP

---

