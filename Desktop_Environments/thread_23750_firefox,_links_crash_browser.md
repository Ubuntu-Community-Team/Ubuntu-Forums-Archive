---
title: "firefox, links crash browser"
date: 2005-04-03
forum: Desktop Environments
---

### Post by juniper on 2005-04-03
hello, i am running warty on a laptop (dell).
i have both

mozilla                1.7.3-1ubuntu1
mozilla-firefox        0.99+1.0PR.1+revertedt

and both browsers have displayed the recent behaviour that any download link crashes the browser (even right clicking and picking "download link" does this.  is anyone else experiencing this?

this is the most up to date firefox and ubuntu (at least with my systems apt-get).

j

---

### Post by Leif on 2005-04-04
I don't use warty, so I don't know if this is relevant, but if you've got an nvidia card, renderaccel seems to be causing problems right now. Edit your xfree configuration file to comment out the line with it.

---

### Post by bored2k on 2005-04-04
[QUOTE=juniper]hello, i am running warty on a laptop (dell).
i have both

mozilla                1.7.3-1ubuntu1
mozilla-firefox        0.99+1.0PR.1+revertedt

and both browsers have displayed the recent behaviour that any download link crashes the browser (even right clicking and picking "download link" does this.  is anyone else experiencing this?

this is the most up to date firefox and ubuntu (at least with my systems apt-get).

j[/QUOTE]
 If you want a more up to date Firefox, visit [http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/) and get their warty repositories. Or download from mozilla.org

---

### Post by juniper on 2005-04-04
> 
If you want a more up to date Firefox, visit [http://backports.ubuntuforums.org/](http://backports.ubuntuforums.org/) and get their warty repositories. Or download from mozilla.org


i just went to the backports site and there is something about updating before april 1 as the ubuntu-bp will be permanently disabled.  it is april 4 now, can i still do it?

j

---

### Post by Leif on 2005-04-05
It's only ubuntu-bp.sourceforge.net that's getting disabled, [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) still works. Add these to your sources.list :

deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) warty-backports main universe multiverse restricted
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) warty-extras main universe multiverse restricted

Keep in mind that hoary is getting released tomorrow tho, so you might just want to upgrade to that instead.

---

