---
title: "Make Autostart apps start in tray"
date: 2009-11-26
forum: Desktop Environments
---

### Post by bruno321 on 2009-11-26
(Kubuntu 9.10) In the Autostart directory I have links to Akregator and Kmail, so they start automatically when I boot up. But they always start maximized: I want them to start directly in the tray (that is, not even minimized). How could I do it?

Thanks

---

### Post by Zorael on 2009-11-27
Is that possible?

KWin allows you to set up rules for windows, like confining them to a specific desktop, making them not show up in the panel task list, keep above/below, transparency when focused/unfocused, etc. One of them is *Minimized*, which you can set to *Force Initially*. I *imagine* that would make it minimized upon start of it, but unless the app itself is set up to go to the tray when minimized instead of to the task list, like Kopete/Amarok/KTorrent/etc supports, I'm not sure it's possible.

Open up the window operations menu (alt+f3, or by clicking the little icon to the top left of a window) and either pick *Advanced -> Special Window Settings* to set rules for that particular window of that app, or *Special Application Settings* to set a rule for **all** windows of that app.

---

