---
title: "XFCE Systray not working"
date: 2005-11-10
forum: Desktop Environments
---

### Post by 23meg on 2005-11-10
I'm trying to add a notification area to the XFCE panel with the systray plugin but when trying to add it I get the message "Could not create panel item 'Systemtray'" and nothing happens.

This is with XFCE 4.2.2. Any ideas?

---

### Post by etc on 2005-11-10
The taskbar on the top in the default setup has a systray and you can't have both running for some reason.
Either kill the taskbar or go to the XFCE control panel and select taskbar and uncheck  "Show system tray in taskbar".
Then try to load the plugin in the panel again.

---

### Post by 23meg on 2005-11-10
Thanks, that did it. I still can't get Alltray to display icons in the tray though; I'd appreciate help on this.

---

### Post by funkydan2 on 2005-11-10
What icons are you expecting there?

If you start gaim for example, do you get the yellow human looking icon in the system tray?

---

### Post by 23meg on 2005-11-11
Everything except Alltray works.

---

