---
title: "Nautilus 13.04 Theme Help - Only Ambiance Shows Places / Top Icons Properly"
date: 2013-05-11
forum: Desktop Environments
---

### Post by own3mall on 2013-05-11
Hi All,

I decided to try the Luna theme, which I upgraded to gtk3, on Ubuntu 13.04.  Compared to Ubuntu 12.04, a lot of things are not displaying properly when using this theme on Ubuntu 13.04.  I can't figure out what's wrong though, as I've looked through the latest Ambiance theme code, and I can't seem to hunt down a couple of new icons Nautilus 3.6 is using.  The Luna theme would look fine on Ubuntu 13.04 if Nautilus would use the icons it uses in the Ambiance theme.  I looked for these icons in the Ambiance theme (/usr/share/icons/ubuntu-mono-dark/), searched every folder of the theme, and could not find them.

These are the icons I'm talking about:

[[IMG]http://s12.postimg.org/gkqy9x995/where_are_the_nautilus_icons.jpg[/IMG]]("http://postimg.org/image/gkqy9x995/")

Notice the magnifying glass for example.  With the Luna theme and other stock themes in Ubuntu 13.04, Nautilus looks like this:

[[IMG]http://s22.postimg.org/vremxbmnx/these_icons.jpg[/IMG]]("http://postimg.org/image/vremxbmnx/")

Any idea what needs to be done?  All help is appreciated.

---

### Post by mc4man on 2013-05-11
Those are symbolic icons in gtk buttons

/usr/share/icons/gnome/scalable/

---

### Post by own3mall on 2013-05-11
> **mc4man said:**
> Those are symbolic icons in gtk buttons

/usr/share/icons/gnome/scalable/

Thanks.  Do you have any idea why Ambiance is the only theme properly using these icons?  I see nothing in the Ambiance config / theme files stating to use these icons with Nautilus?

---

### Post by mc4man on 2013-05-12
> **own3mall said:**
> Thanks.  Do you have any idea why Ambiance is the only theme properly using these icons?  I see nothing in the Ambiance config / theme files stating to use these icons with Nautilus?
Not a clue though light-themes/ubuntu-mono has been doing so for quite some time,. Just seems to use what nautilus-3.6+ uses..
(For instance if I want to change/add a button to the nautilus toolbar I do so in nautilus's source & it comes out as intended/edited to.

---

### Post by own3mall on 2013-07-07
I'm not sure when it changed, but it looks like Ubuntu updated Nautilus to fix this issue.  Works fine, and I didn't make any changes to the theme.  Granted, there are still a few issues with the theme that I need to look into, but the icons mentioned in the OP are working now.

---

