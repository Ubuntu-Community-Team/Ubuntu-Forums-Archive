---
title: "Simple login and banner"
date: 2009-11-02
forum: Desktop Environments
---

### Post by gwidion on 2009-11-02
To any that can help,

My company allows me to use ubuntu at work if I comply with some simple security directives, like: don't list users on your login screen, do display the approved banner text prior to login, etc.  With 9.04, this was pretty easy with the InfoMsgFile entry in gdm.conf.  I have tried to use the Configuration editor and gconf-editor to modify /apps/gdm/simple-greeter settings, but things still don't work.  More importantly, simple common requirements like these are becoming more difficult to find and manage, not easier, as things should be in newer, 'better', versions of the software.  I know this is more if a gnome issue than an ubuntu one, but...

Thanks to anyone that help me continue to use the product!

---

### Post by Kushkah on 2009-11-02
After changing disable_user_list banner_message_enable and banner_message_text_nochooser ( Which it looks you did already, just making sure ;) ).  Right-click each one and click Set as Mandatory.  That should do it.

---

### Post by earthpigg on 2009-11-03
[http://en.wikipedia.org/wiki/SLiM](http://en.wikipedia.org/wiki/SLiM)

vanished from the 9.10 repos, but the 9.04 .deb downloadable [here]("http://en.wikipedia.org/wiki/SLiM") works in 9.10 without modification.
```

sudo dpkg -i /path/to/package.deb
```

---

### Post by earthpigg on 2009-11-03
also, you could give gdm-2.20 a shot.

[http://packages.ubuntu.com/karmic/gdm-2.20](http://packages.ubuntu.com/karmic/gdm-2.20)

---

