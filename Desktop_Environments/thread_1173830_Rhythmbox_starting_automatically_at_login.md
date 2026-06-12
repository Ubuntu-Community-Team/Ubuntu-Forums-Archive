---
title: "Rhythmbox starting automatically at login"
date: 2009-05-30
forum: Desktop Environments
---

### Post by b@sh_n3rd on 2009-05-30
Hi, a couple of days ago, I set up Rhythmbox and Emesene to load at login. Then, yesterday, I removed emesene and just unchecked next to "Rhythmbox" in "**Startup Applications**". After this, Rhythmbox still loaded automatically at login. So, I just removed that command all together from the Startup Applications applet. Even though I did this, Rhythmbox still loads automatically at each login. How can I fix this?...Thanks for any replies...

---

### Post by kpkeerthi on 2009-05-30
Delete the corresponding .desktop file from ~/.config/autostart. Do you have 'Save Session" option turned on?

---

### Post by b@sh_n3rd on 2009-05-30
> **kpkeerthi said:**
> Delete the corresponding .desktop file from ~/.config/autostart. Do you have 'Save Session" option turned on?

Nothing there but **cairo-dock**. Save Session? You mean like in Startup Aplications, on the Options tab? Nope, that option is unchecked...thanks for your reply btw..

---

