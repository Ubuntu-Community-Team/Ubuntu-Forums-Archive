---
title: "Openbox .xinitrc / autostart.sh / nm-applet problems"
date: 2009-12-01
forum: Desktop Environments
---

### Post by pantone186 on 2009-12-01
Hello,


Using openbox on a minimal debootstraped 9.04 install, without a login manager i.e. using startx


If I use autostart.sh by itself nm-applet starts fine.

However if I use exec openbox-session in .xinitrc nm-applet won't start.

Both .xinitrc and autostart.sh are read/writable by user, and readable by all others.

If I add user NOPASSWD for nm-applet using visudo the applet starts but requires entry of the network's pre-shared-key (PSK).


I don't understand whats going wrong here as (in the first instance) .xinitrc calls openbox-session which calls autostart.

---

### Post by urukrama on 2009-12-04
I don't use nm-applet, but other users have had similar issues. It might just be that nm-applet is loaded before X and Openbox are fully loaded -- if that is the case, try using the following command:

> (sleep 2 && nm-applet) &

The following thread offer various other solutions; perhaps one of them will help you. The user in that thread uses LXDE (instead of plain Openbox), but that shouldn't be an issue.

[http://ubuntuforums.org/showthread.php?t=1089646&highlight=nm-applet+openbox](http://ubuntuforums.org/showthread.php?t=1089646&highlight=nm-applet+openbox)

In case you really don't get it to work, and you'd like to stick with Openbox, you can also try wicd as a replacement for nm-applet.

---

### Post by pantone186 on 2009-12-06
Hello Urukrama,

I'm afraid Iv'e had no luck at all using openbox-session, only autostart used by itself works. Which is ok I suppose.

I have no idea why openbox-session works for some people and not others?

I'm also struggling to start another program sjog (sony jog dial)

I have to admit I'm not sure why openbox-session is needed.

Also the global autostart file in /etc/xdg/openbox makes a call to /etc/xdg/autostart which contains nm-applet.desktop. This should autostart but it doesn't.


Its seems strange to me that their should be so many autostart methods, especially as they don't work!


I've tried wicd before in an attempt to reduce gnome deps, but it doesn't support 3g/wifi combo cards.


Nice website by the way very helpful and interesting read.

---

