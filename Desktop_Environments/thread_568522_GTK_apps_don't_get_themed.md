---
title: "GTK apps don't get themed"
date: 2007-10-05
forum: Desktop Environments
---

### Post by Adamal on 2007-10-05
I'm using 7.10 beta right now, although I've noticed this in other version of Ubuntu.  If I change the default controls under apperence, gtk2 and other gnome apps are themed just fine.  However GTK apps like Synaptic and the update utility are always displayed as un-themed, unless I'm either using Clearlooks or Human as my themes.  How do I get other themes to style GTK apps?

---

### Post by ryanVickers on 2007-10-05
that's because your running them as root - move the themes from /home/username/.themes to /usr/share/themes I think, and it should work (you might have to turn the theme off and on again...)

this just doesn't apply to icons and window borders because that is within your session, but window borders are included here...
The icons are unser the same paths, just ".icons" or "icons" instead of "themes" or ".themes"

---

### Post by Adamal on 2007-10-05
Thanks.  

They really need to have the option to install the theme for all users or just yourself.

---

### Post by ryanVickers on 2007-10-05
Yeah, that's so annoying eh?!  It's great how Linux can keep the themes and that totally separate for each person, but then there should be a "you" or "all" or "all and root" option, and you just enter the root password or something...

Unlike windows, everyone shares one recycle bin! :p  Not kidding! :)

---

