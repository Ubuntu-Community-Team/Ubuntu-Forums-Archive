---
title: "Setting and Using Panel Backgrounds in Gnome"
date: 2005-12-10
forum: Desktop Environments
---

### Post by audax321 on 2005-12-10
Hello,

I was wondering if someone could do the following and let me know what happens:

1. Right click an existing panel and make a new panel.
2. Right click the new panel and go to properties > background.
3. Tell it you want to use a background image and then download and use this image: [panel-top-1280-SoapSkyBlue.png]("http://www.dieburnbot.com/panel-top-1280-SoapSkyBlue.png")
4. Close the properties dialog and right click the panel > add to panel > and add the CLOCK applet.

Now, I used to use this background in Hoary and the background came through the clock applet. But, in Breezy, the clock applet blocks out the background for me. Any idea why this is? Does it happen to you as well?


EDIT: Never mind, it appears to be a problem with the theme I'm using. The theme is: [http://www.gnome-look.org/content/show.php?content=32227](http://www.gnome-look.org/content/show.php?content=32227)

So new question, anyone know how to edit this theme so it lets the panel background come through? Any help is much appreciated. Thank you. I'll post on gnome-look as well.

---

### Post by audax321 on 2005-12-10
Well that was easy. I just opened the theme's GTKRC and commented out the line that included the file 'panel.rc' and it got rid of the panel background that was set by the theme so I could use mine.

---

