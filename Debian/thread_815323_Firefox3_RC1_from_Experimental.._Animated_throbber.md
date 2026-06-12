---
title: "Firefox3 RC1 from Experimental.. Animated throbber gone!"
date: 2008-06-01
forum: Debian
---

### Post by kalpik on 2008-06-01
Hi!

I was running FF3b5 from experimental since a long time and all was well.. But i recently updated to FF3 RC1 from experimental itself, and now the throbber (the icon that comes on the left side of every tab that is loading something) is static and does not rotate. On further investigation, i also saw that Animated PNGs, a new feature in FF3, are not getting animated either. Have a look at this page for checking animated PNGs: [http://labs.mozilla.com/2007/08/better-animations-in-firefox-3/](http://labs.mozilla.com/2007/08/better-animations-in-firefox-3/)

Is anyone else also facing the problem?

Edit: Oops.. I meant Iceweasel instead of Firefox :P

---

### Post by jdhore on 2008-06-01
I've noticed this as well...I have a pretty simple fix, but it will only work if you're on amd64....

---

### Post by kalpik on 2008-06-01
Yes, Im on amd64. Can i have the fix please? :)

---

### Post by jdhore on 2008-06-01
> **kalpik said:**
> Yes, Im on amd64. Can i have the fix please? :)

[http://ftpmaster.defusion-project.org/archive/pool/main/x/xulrunner-1.9/xulrunner-1.9-gnome-support_1.9~rc1+nobinonly-0+1_amd64.deb](http://ftpmaster.defusion-project.org/archive/pool/main/x/xulrunner-1.9/xulrunner-1.9-gnome-support_1.9~rc1+nobinonly-0+1_amd64.deb)

[http://ftpmaster.defusion-project.org/archive/pool/main/x/xulrunner-1.9/xulrunner-1.9_1.9~rc1+nobinonly-0+1_amd64.deb](http://ftpmaster.defusion-project.org/archive/pool/main/x/xulrunner-1.9/xulrunner-1.9_1.9~rc1+nobinonly-0+1_amd64.deb)

[http://ftpmaster.defusion-project.org/archive/pool/main/f/firefox-3.0/firefox-3.0-gnome-support_3.0~rc1+nobinonly-0+2_amd64.deb](http://ftpmaster.defusion-project.org/archive/pool/main/f/firefox-3.0/firefox-3.0-gnome-support_3.0~rc1+nobinonly-0+2_amd64.deb)

[http://ftpmaster.defusion-project.org/archive/pool/main/f/firefox-3.0/firefox-3.0_3.0~rc1+nobinonly-0+2_amd64.deb](http://ftpmaster.defusion-project.org/archive/pool/main/f/firefox-3.0/firefox-3.0_3.0~rc1+nobinonly-0+2_amd64.deb)

Install those debs...That's Firefox 3 RC1 from Ubuntu Intrepid recompiled for Lenny (or Sid) and i can guarantee APNG's work in it.

---

### Post by kalpik on 2008-06-02
Hmm.. ok. So that's firefox. I thought you'd give me something for iceweasel. Anyway, ill try that once im back at home. Thanks :)

---

