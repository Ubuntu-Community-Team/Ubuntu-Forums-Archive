---
title: "Gibbon: Appearance Properties-&gt;Backgrounds (adding more universally)"
date: 2007-09-26
forum: Desktop Effects &amp; Customization
---

### Post by expert01 on 2007-09-26
I have a bunch of backgrounds I want to be available to all users. I've added them to /usr/share/backgrounds, but I don't know how to get them all to appear in the Appearance Preferences Background without adding each one one each user account. Is there perhaps a command to run, or a config file to remove to reset the list?


*edit* never mind. I ended up opening the Add in the backgrounds section, where I found I could select multiple backgrounds to add. I then added all backgrounds, closed the Appearance Preferences window, and copied the backgrounds.xml from ~/.gnome2 to /home/*/.gnome2

 sudo cp ~/.gnome2/backgrounds.xml /home/*/.gnome2/

---

