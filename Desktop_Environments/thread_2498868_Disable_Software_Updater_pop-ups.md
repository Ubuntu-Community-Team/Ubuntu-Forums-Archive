---
title: "Disable Software Updater pop-ups"
date: 2024-07-01
forum: Desktop Environments
---

### Post by currentshaft on 2024-07-01
3d

---

### Post by Rubi1200 on 2024-07-02
Settings >> Notifications >> scroll down to Software Updater and turn off.

Problem solved?

---

### Post by currentshaft on 2024-07-02
dls

---

### Post by &amp;KyT$0P# on 2024-07-02
Can you just uninstall update-notifier?  Or disable it from auto-starting (delete [FONT=monospace]/etc/xdg/autostart/update-notifier.desktop[/FONT])?

---

### Post by #&amp;thj^% on 2024-07-02
> **halogen2 said:**
> Can you just uninstall update-notifier?  Or disable it from auto-starting (delete [FONT=monospace]/etc/xdg/autostart/update-notifier.desktop[/FONT])?

+1 That's how i do it.
```
sudo mv /etc/xdg/autostart/update-notifier.desktop /home/me/Documents 

```
You can move it to your desired location

Also there are methods to use if your not content with what's provided here.

---

### Post by deadflowr on 2024-07-02
```
gsettings set com.ubuntu.update-notifier no-show-notifications true
```
Also try to set system settings > apps > software updater and turn show notifications to off. 

And disable or remove snap-store since it too can do updates, I guess.
But I expect that already done. In one way or the other.

See if the helps.

---

