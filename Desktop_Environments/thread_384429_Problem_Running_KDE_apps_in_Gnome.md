---
title: "Problem Running KDE apps in Gnome"
date: 2007-03-14
forum: Desktop Environments
---

### Post by chriscando on 2007-03-14
Hello, I can run KDE apps just fine in Gnome but the performance is off. The redraw times are really slow. For example, when I drag a window over konqueror, the konqueror window turns gray and takes a few seconds to redraw. I only have this problem with KDE apps too, like amarok.

When I first installed Ubuntu this wasn't a problem, but I seem to have done something to change this.  Does anyone have any ideas on how I can fix this?

---

### Post by Songwind on 2007-03-14
> **chriscando said:**
> Hello, I can run KDE apps just fine in Gnome but the performance is off. The redraw times are really slow. For example, when I drag a window over konqueror, the konqueror window turns gray and takes a few seconds to redraw. I only have this problem with KDE apps too, like amarok.

When I first installed Ubuntu this wasn't a problem, but I seem to have done something to change this.  Does anyone have any ideas on how I can fix this?

Do you have compositing, like transparency and drop-shadows, turned on?

I found that GTK apps in KDE had similar issues when I was running with transparency on.

---

### Post by chriscando on 2007-03-14
Thanks for the suggestion, I don't have any transparency effects turned on. Would these be KDE settings? I can look into this.

I dont know what I did, maybe it was something I installed or changed in xorg.conf.

---

### Post by chriscando on 2007-03-14
Ohh thanks, you are correct. In KDE Control Center > Apperance & Themes > Style > Effects   I turned off GUI effects and that seemed to correct everything. Thanks for pointing me in the right direction :)

---

