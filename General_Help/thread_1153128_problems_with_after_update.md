---
title: "problems with after update"
date: 2009-05-08
forum: General Help
---

### Post by supermooshman on 2009-05-08
I have installed the ubuntu netbook remix - worked like a dream


Untill... when I got the updates.
After the updates:

[LIST]
[*] my panel bars dissapeared
[*]my windows don't have the top bar anymore
[*]alt + click (move) doesn't work anymore
[/LIST]
Has anyone encountered this, and more importantly, does anyone know how to go back to the previous layout?

Cheers

---

### Post by supermooshman on 2009-05-08
I think this [https://bugs.edge.launchpad.net/desktop-switcher/+bug/349519](https://bugs.edge.launchpad.net/desktop-switcher/+bug/349519) might be the answer, is there anyone who might translate this to stupid people(me) language?

Thanks

---

### Post by Brandon Williams on 2009-05-08
The bug has [this attached .deb](http://launchpadlibrarian.net/26020903/desktop-switcher_0.4.6_i386.deb). Download and install it, and then use the desktop switcher to switch back-and-forth between classic mode and netbook-remix mode. This should clear up the problem (according to reports in the bug discussion).

After downloading the .deb file, run this command to install it: "sudo dpkg -i desktop-switcher_0.4.6_i386.deb".

---

