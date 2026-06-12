---
title: "[SOLVED] How do I make Fluxbox an option as a session?"
date: 2008-12-19
forum: Desktop Environments
---

### Post by maphco on 2008-12-19
Through trying things for the last couple hours I finally got to "make install" fluxbox.  However, when I went to use it as a session it wasn't listed.

I followed the steps on this page: [http://fluxbox-wiki.org/index.php?title=Faqs#How_do_I_add_fluxbox_to_my_GDM_sessions_menu.3F](http://fluxbox-wiki.org/index.php?title=Faqs#How_do_I_add_fluxbox_to_my_GDM_sessions_menu.3F)

Which were:





Create the file: /etc/gdm/Sessions/fluxbox with contents:

#!/bin/sh
#
# /etc/gdm/Sessions/fluxbox
#
# global fluxbox session file -- used by gdm
exec /etc/X11/Xsession /usr/bin/fluxbox

Of course, change /usr/bin/fluxbox to wherever your fluxbox binary is. If the /etc/gdm directory doesn't exist, it may be /etc/X11/gdm/Sessions/fluxbox on your computer. 





That didn't seem to work. Any tips?

---

### Post by maphco on 2008-12-19
I continued to google and found this page: [http://ubuntuforums.org/archive/index.php/t-499188.html](http://ubuntuforums.org/archive/index.php/t-499188.html)

It worked... it finally worekd... I actually just cried I'm so happy! :D Over five hours of googling and fiddling and I finally got it! WOOOOOOOO HOOOOOOOO!

---

### Post by hzsirmar on 2008-12-19
[Shenzhen GuoShi Lighting Industrial Co., Ltd](http://www.alilinks.com/manufactures/1022/Shenzhen-GuoShi-Lighting-Industrial-Co-Ltd.htm)Shenzhen Guoshi Lighting Company is specialized in manufacturing High Power LED Lighting. We have excellent development team and strong technological power. Our staff insists on the enterp [http://www.alilinks.com/manufactures/1022/Shenzhen-GuoShi-Lighting-Industrial-Co-Ltd.htm](http://www.alilinks.com/manufactures/1022/Shenzhen-GuoShi-Lighting-Industrial-Co-Ltd.htm)

---

