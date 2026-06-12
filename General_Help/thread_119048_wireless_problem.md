---
title: "wireless problem"
date: 2006-01-18
forum: General Help
---

### Post by Zaventh on 2006-01-18
I have a notebook with KDE 3.5 and an ipw2100 wireless card. Recently, as I have been using the wifi connection, it will just stop working. I open up kwifimanager and see that it apparently has connected to an Apple networks ad-hoc access point, although there are none around (and it happens at locations miles apart. the apple network does not exist as far as I know). The problem is worked around by reactivating the proper protocol and issuing an ifdown eth0 && ifup eth0. What could be causing this and what can I do to fix it?

---

### Post by jshein on 2006-01-18
I have found kwifimanager to be extremely buggy, and it tends to cause odd problems on certain machines yet work fine on another. Try using wifi-radar as an alternate and see if the problem disapears.

Also you could try looking in /var/log/messages to see if there is anything relating to the new association.

---

### Post by chadwick359 on 2006-01-18
While wifi-radar seems to be most users choice, I have never been a big fan. If I were you, I would grab network-manager and run nm-applet for my wireless needs. Just  a suggestion.

---

