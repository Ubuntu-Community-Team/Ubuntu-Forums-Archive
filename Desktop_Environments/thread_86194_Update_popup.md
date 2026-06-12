---
title: "Update popup"
date: 2005-11-04
forum: Desktop Environments
---

### Post by Chris Cromer on 2005-11-04
How can I disable the new updates available popup? I don't mind the icon appearing on my panel for new updates, but that popup message get's on my nerves, I hated it in windows xp and I hate it now, I can see the icon I don't need a full popup telling me about it.

Not only that but the popup window is stuck on my screen right now, it won't disapear even though I have already installed the updates. Of course I did the updates manually via apt-get update and apt-get dist-upgrade. But chances are that problem is something to do with the fact that I am using dapper drake.

---

### Post by psychicdragon on 2005-11-04
Just kill the process (killall update-notifier) and then save your session when you log out.

---

### Post by Chris Cromer on 2005-11-04
Won't that also stop the icon from appearing? I only want to get rid of the popup, I don't want to get rid of the icon.

---

### Post by psychicdragon on 2005-11-04
True. Unless there is a preference option or gconf key, that's your only recourse. Other than taking a look at the source yourself, or filing a bug report/feature request that is.

---

