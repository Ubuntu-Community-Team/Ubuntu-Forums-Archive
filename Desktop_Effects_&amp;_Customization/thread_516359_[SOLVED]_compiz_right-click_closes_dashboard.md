---
title: "[SOLVED] compiz: right-click closes dashboard"
date: 2007-08-03
forum: Desktop Effects &amp; Customization
---

### Post by dbbolton on 2007-08-03
when i hit F9 to view my "dashboard" in compiz, all of my screenlets show up fine, but when i right-click on them, the dashboard closes, and returns to the normal desktop. i thought that you could right-click on the screenlets in order to change their settings. 

so, how can i make it so that a right-click doesn't close the dashboard?

---

### Post by darqfaux on 2007-08-03
I had this problem at first too. It seems if you go to **System-->Preferences-->CompizConfig Settings Manager**. Then click **Utility** and make sure ***Workarounds*** is unchecked. That should enable you to right click your widgets!:)

---

### Post by Inxsible on 2007-08-03
> **darqfaux said:**
> I had this problem at first too. It seems if you go to **System-->Preferences-->CompizConfig Settings Manager**. Then click **Utility** and make sure ***Workarounds*** is unchecked. That should enable you to right click your widgets!:)

Thanks for pointing this out. But i did some trial and error and it seems that you don't need to uncheck the entire Workarounds. Go into it, and simply uncheck Qt Window Fix which makes perfect sense, since i think screenlets were built on Qt libraries or at least that's what I read somewhere.

---

### Post by dbbolton on 2007-08-03
it's working fine now. thank you both :)

---

