---
title: "&quot;Show desktop&quot; icon missing"
date: 2005-02-10
forum: Desktop Environments
---

### Post by mglukhovsky on 2005-02-10
After playing around with a lot of themes and icons to get that ideal desktop look  :-)  which I am finally getting close to. Oddly enough, in the process of changing themes etc., I lost the "Show desktop" icon as seen in the image below. It's missing from both the bottom panel and the "Computer" menu at the top. 
I found a few keys for the GNOME confuration using Gconf that seem to be appropriate for assigning a custom icon, but unfortunately they have no effect. They are as follows:
* /apps/panel/default_setup/applets/show_desktop_button
* /apps/panel/profiles/default/applets/show_desktop_button

This is incredibly frustrating, so if anyone knows where the configuration file defining the location of the Show Desktop button is so I don't have this annoying red x at the bottom of my screen.

Screenshot to better understand my problem (look at the bottom):
[http://team-rex.net/linux/missing_icon.jpg](http://team-rex.net/linux/missing_icon.jpg)

---

### Post by Greg T. on 2005-02-10
Same thing happened to me tonight when I upgraded on Hoary. I lost the show desktop icon, computer icon (in the file browser), folder icons (in the file browser), and the trash bin icon. Switching to the default "Human" theme got the icons back for me.

I then removed the theme I had been using ("Indubstrial") and reinstalled it. Everything's fine now.

---

### Post by mglukhovsky on 2005-02-11
That did it, thanks. Although I didn't need to reinstall any themes- just switched to the defaults, restarted GNOME, switched back to my setup and everything worked beautifully.

---

### Post by reddfox321 on 2007-06-12
how do you restart gnome?

---

