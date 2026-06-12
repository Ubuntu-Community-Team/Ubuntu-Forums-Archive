---
title: "can't configurate plugins in ePSXe"
date: 2006-11-11
forum: Gaming &amp; Leisure
---

### Post by matemargo on 2006-11-11
I have read several HOWTOs, and finally I can run ePSXe.
The problem now is that I can't configure the plugins (audio or video).
When I open the config dialog I can't choose which plugin to use, I only see the "DISABLED" text.

Here are the screenshots:

[http://img175.imageshack.us/my.php?i...igsoundyh6.png](http://img175.imageshack.us/my.php?i...igsoundyh6.png)

[http://img140.imageshack.us/my.php?i...igvideomf0.png](http://img140.imageshack.us/my.php?i...igvideomf0.png)

Does anyone know why the config has this behavior?

---

### Post by hikaricore on 2006-11-11
For some reason I can't load your screenshots, but I'm going to guess that you havn't created your plugins directory or not installed any plugins.  Check this thread to see if you missed anything: [http://www.ubuntuforums.org/showthread.php?t=95835]("http://www.ubuntuforums.org/showthread.php?t=95835")

---

### Post by matemargo on 2006-11-13
I had to rename the **plugin** directory to **lib** in order to avoid the crashing when I open the dialog.

PS: The screenshot shows the config dialog with only 1 option in the plugin list dropdown: DIABLED.

---

### Post by hikaricore on 2006-11-13
If you renamed the plugin directory i don't have to imagine too much to figure out why you're getting Disabled as the only option.  You renamed the plugin directory..  if it was crashing you may want to try reinstalling it, or compiling it yourself.  I've never had epsxe crash just from opening the config window.

---

