---
title: "How do I disable the ALT key?"
date: 2007-10-23
forum: Desktop Environments
---

### Post by godrox on 2007-10-23
I'm creating a kiosk based on xubuntu using Firefox and the kiosk extension, but I need to disable the ALT key to prevent people from doing things like ALT+F4, CTRL+ALT+DEL, ALT+F2, etc. I've searched around and haven't found anything on this. Any suggestions how how to do this?

---

### Post by ofb on 2007-10-23
I think you want xmodmap. Do 'man xmodmap' in terminal to have a look.

Last time I messed with this I used xkeycaps, via synaptic.
[http://www.jwz.org/xkeycaps/](http://www.jwz.org/xkeycaps/)

---

### Post by godrox on 2007-10-23
Okay, thanks! I'll check it out.

---

### Post by godrox on 2007-10-24
xkeycaps is exactly what I needed. Thank you!

Now my problem is that I want to display the navigation and address bar for R-Kiosk extension for Firefox, but it also displays the minimize, restore and close buttons in the upper right-hand corner. Is there a way to remove or disable these buttons without removing the navigation and address bar?

---

### Post by ofb on 2007-10-24
Uh-oh...
[http://www.mail-archive.com/project_owners@mozdev.org/msg02747.html](http://www.mail-archive.com/project_owners@mozdev.org/msg02747.html)

> R-Kiosk extension that allows the browser to go to full screen (including no
windows title bar, minimize, maximize, and close buttons) has broken since the
last FF update (2.0.0.2) and the author has not logged in since October 2006. 
See
[https://addons.mozilla.org/firefox/1659/](https://addons.mozilla.org/firefox/1659/)
. Since the last FF update, the extension&#8217;s fullscreen features no longer
work and the windows title bar, minimize, maximize, and close buttons are
enabled.

I'm not familiar with the project, but maybe you better do a little research to see if that got fixed.

... which also suggests that one wouldn't want the browser to do auto-updates, since those are notorious for breaking extensions. But that also means you wouldn't get security updates automatically. So I guess any kiosk setup would need regular sys admin oversight.

Which is obvious I suppose, but didn't occur to me till just now.

Maybe have a look at the Opera version? That would avoid the Firefox extension business.
[http://www.opera.com/support/mastering/kiosk/](http://www.opera.com/support/mastering/kiosk/)

---

### Post by godrox on 2007-10-24
That's odd because it's working fine for me. I just need to know how to remove the minimize/restore/close buttons. Opera's Kiosk Mode looks better anyway. It basically does the same thing I'm doing in Firefox with a bunch of different extensions working together. I'll give it a try.

---

### Post by ofb on 2007-10-25
Are you using 7.10? Under System > Administration, take a look at the new item, Lockdown Editor.

That's in Edubuntu 7.10 anyway. If it's not right there in Ubuntu, then just check Synaptic of course.

---

### Post by godrox on 2007-10-25
> **ofb said:**
> Are you using 7.10? Under System > Administration, take a look at the new item, Lockdown Editor.

That's in Edubuntu 7.10 anyway. If it's not right there in Ubuntu, then just check Synaptic of course.
I don't see it in Xubuntu. I'll check Synaptic. Thanks for the suggestion!

---

