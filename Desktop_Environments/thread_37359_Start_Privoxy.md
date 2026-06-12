---
title: "Start Privoxy"
date: 2005-05-26
forum: Desktop Environments
---

### Post by Frihet on 2005-05-26
I've got to write this down somewhere.

I just installed Privoxy.  I know I have to set it to start on boot.  I just don't know where to do that.

Thanks!

---

### Post by Ufo on 2005-05-27
Hi

 When I installed Privoxy (from synaptic), all I needed to do was set webbrowser (firefox) to use it as proxy in firefox settings.

Privoxy installation took care of starting it up at boot.
There is link named @S20privoxy in /etc/rc2.d which starts it at boot.
Other /etc/rc... directories have their privoxy links too, which where created when privoxy was installed.

If you have this link too, and your default runlevel is 2 (can be seen in /etc/inittab, 2 is default after installation) then it will be started at boot.

Hope this helped and was not too confused description  :-P 

ps. I'm using Ubuntu (Gnome), not Kubuntu (KDE) but I think it doesn't matter.

---

### Post by Frihet on 2005-05-27
Hi, Ufo.

You were right. It was running.  I was still in in a SUSE mindset.

I'm good to go on the browser now.

---

