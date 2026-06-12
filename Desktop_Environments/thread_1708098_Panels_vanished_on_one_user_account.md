---
title: "Panels vanished on one user account"
date: 2011-03-16
forum: Desktop Environments
---

### Post by Bearly Able on 2011-03-16
Hi,

An elderly friend has a system running Xubuntu 10.04.  It was fine the last time she shut down, but when I restarted it yesterday, the panels were missing on her desktop.  I'm not very familiar with Xubuntu, but I looked under XFCE System Settings (or something similar) and found a "Panels" option; however, clicking on this does not open the panels dialogue.

There is a second user account on the machine.  The panels on that are unaffected and I can open the panels dialogue from the XFCE System Settings.

I'd be grateful for any assistance in restoring the panels for the main user account.

Thanks in advance.

Lesley

---

### Post by Jose Catre-Vandis on 2011-03-16
Try opening a terminal and typing:

```
xfce4-panel
```

If panels appear then close terminal, panels will disappear. Then press ALT+F2 type xfce4-panel and press return. Panels should be there. With any luck, they'll be there on reboot too. Otherwise you'll need to add the command to your startup somewhere

---

### Post by Bearly Able on 2011-03-16
Thank you.  I won't get a chance to try this until Friday, but I'll post back the results.

---

### Post by hhh on 2011-03-16
> **Jose Catre-Vandis said:**
> If panels appear then close terminal, panels will disappear. Then press ALT+F2 type xfce4-panel and press return. Panels should be there. With any luck, they'll be there on reboot too. Otherwise you'll need to add the command to your startup somewhere
With xfce4-panel running, go to Settings>>Session and Startup>>Session and make sure the xfce4-panel "Restart Style" is set to Immediately and when you logout check the box for "Save session for future logins" (this is enabled in the "General" tab of Session and Startup, check "Prompt on logout").

---

### Post by Bearly Able on 2011-03-18
> **Jose Catre-Vandis said:**
>  With any luck, they'll be there on reboot too.

And they were. :)  Thanks for your help.

---

