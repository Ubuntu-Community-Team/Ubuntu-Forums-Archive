---
title: "Ubuntu Herd 2 -- I386 Alternate CD Virtual PC '04"
date: 2007-01-14
forum: Development CD/DVD Image Testing
---

### Post by spd106 on 2007-01-14
Test case type: Ubuntu Herd 2 -- I386 Alternate CD
Image ID: 20070111.1
Date of testing: 2007-01-14
md5sum confirmed: Yes
Pass/Fail: [COLOR="Lime"]Pass[/COLOR]
Bugs: [#79117]("https://bugs.launchpad.net/ubuntu/+bug/79117"), [#79254]("https://bugs.launchpad.net/ubuntu/+bug/79254") and [#59618]("https://bugs.launchpad.net/ubuntu/+bug/59618")

Installation was extremely slow. At first I thought it had crashed, changing to alt-f4 showed "kernel: not found." about six times every second. The progress bar disappeared but would return every few minutes as the install carried on. Eventually after about four/five hours it was finished. The syslog weighs in at 11MB!

After install the default colour is reset to 24 bit, which is wrong so I had to boot in safe mode to edit the /etc/X11/xorg.conf.

Finally the mouse capture doesn't work just like on the desktop cd live environment.

---

### Post by Henrik on 2007-01-14
Can you click with the mouse and it just doesn't get captured?

---

### Post by spd106 on 2007-01-14
Yes, it's rather weird to describe. Normally when you click on the window the mouse is grabbed by vpc (with a warning) and you can't leave the window unless you release it by pressing Alt Gr. But on Herd 2 it never gets grabbed.

If a click on the window then I get a square with a dashed outlline, like in an image editor. None of the icons on the ubuntu desktop show any sign of being selected.

I'm dual booting edgy and win2k with virtual pc 2004, the freely downloadable edition. We use it at Uni (MSDNAA) for network simulation. I've shown Ubuntu to the program leader and he's interested in using it, but every time he tries it something like this goes wrong. Dapper isn't too bad, but Edgy was awful. This mouse thing is new though, I'm hoping it's just a new kernel (2.6.20) problem that can be resolved.

Any ideas?

---

