---
title: "lost network manager"
date: 2009-02-10
forum: General Help
---

### Post by sjewenp on 2009-02-10
i'm a ubuntu novice.
i thought i'd get all fancy and moved all my icons and stuff to the bar on the bottom and erased the bar on the top.
in the process i lost my network manager icon. (whoops)
it's not under system>admin> and my computer won't let me choose where i connect.  it just randomly picks a network.  i tried downloading various wireless apps, but they don't work.  how do i find network manager and/or restore the icon?
thanks

---

### Post by pytheas22 on 2009-02-10
To launch NetworkManager, you have to open a terminal and type:
```

sudo NetworkManager
```

This should start it, but I think it needs a 'notification area' in which to display its applet.  Maybe your customized panel doesn't have a notification area anywhere; if so, just right-click on the panel, select 'Add to Panel', and select 'Notification Area'.  Then try starting NetworkManager again.

You could also use [wicd]("http://wicd.sourceforge.net"); it works as well as (and sometimes better than) NetworkManager.

---

### Post by sjewenp on 2009-02-11
thanks.
i just erased the notification area.
i am dumb.

---

