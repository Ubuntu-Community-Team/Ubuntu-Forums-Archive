---
title: "GNOME panel background displayed as toolbar background"
date: 2007-07-19
forum: Desktop Environments
---

### Post by wixwod on 2007-07-19
In a couple applications, I've so far only noticed it in Evolution and the Archive Helper, the GNOME panel background appears as the toolbar background. I'm using straight metacity. Does anyone know how to fix it, or is it a problem in the GTK related source code of these individual applications? I'm not sure what else to post that's relevant, but I will post anything else that's needed.

Thanks for your consideration!

[IMG]http://img473.imageshack.us/img473/2089/screenshotol2.png[/IMG]

---

### Post by testube_babies on 2007-07-19
If you're using a theme that defines the gnome-panel background automatically, it will always do this.  I always edit the panel code out of the theme's gtkrc and then set the panel background manually, which avoids this issue.

---

### Post by wixwod on 2007-07-19
Success! Thanks so much for your help.

---

