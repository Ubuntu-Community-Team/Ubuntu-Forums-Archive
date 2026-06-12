---
title: "Different scroll bars with elementary theme"
date: 2010-07-15
forum: Desktop Environments
---

### Post by timbo-lino on 2010-07-15
Hi all,

I installed the elementary theme 1.2.1~ppa106~10.04.

Unfortunally I still get the old scroll bars. Only on applications I start with sudo, like nautilus or synaptic, I get the new scrollbars.

[IMG]http://www.ubuntu-pics.de/bild/105210/20100715_001_cKIV2L.png[/IMG]

What can be the problems here?

Thanks in advance

---

### Post by nilarimogard on 2010-07-15
Weird, usually this happens the other way around. Try this:

```
rm -r ~/.themes/elementary*
sudo apt-get install --reinstall elementary-theme
```

Then select Elementary in the appearance properties and see if you get the new scollbars (in case multiple Elementary themes show up here, try them all - it means you have multiple Elementary themes installed under /usr/share/themes).

---

### Post by timbo-lino on 2010-07-15
Thanks for your help. 

I had the [elementary-mod]("http://gnome-look.org/content/show.php/Elementary-mod?content=119715") installed (for the nautilus breadcrumbs). This  caused the error. Now I deinstalled it and the scroll bars are back again.

In your [blog]("http://www.webupd8.org/2010/04/nautilus-elementary-breadcrumbs-for-any.html") I found a way to get the breadcrumbs anyway :) 

Thanks again!

---

### Post by nilarimogard on 2010-07-16
Also try the [Victory style Nautilus Elementary breadcrumbs]("http://www.webupd8.org/2010/07/victory-yet-another-nautilus-elementary.html") which also works for any theme. It looks very nice:

[IMG]http://lh3.ggpht.com/_1QSDkzYY2vc/TDsOWcaalPI/AAAAAAAABdk/PTdGhZ1-bF0/nautilus-elementary-victory-breadcrumbs.png[/IMG]

---

### Post by timbo-lino on 2010-07-16
Hi nilarimogard,

thanks for the hint. On the screenshots I did not like the Victory style, but live they look much better.

---

### Post by kericw on 2010-12-12
> **timbo-lino said:**
> Hi nilarimogard,

thanks for the hint. On the screenshots I did not like the Victory style, but live they look much better.


exuse me , but i have just suffered from the same problem.  how can i delete the nautilus-mod files.  i can't find it in usr/share/themes/

---

