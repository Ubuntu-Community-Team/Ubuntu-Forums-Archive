---
title: "Decoration settings keeps resetting after reboot"
date: 2011-03-27
forum: Desktop Environments
---

### Post by tpsa on 2011-03-27
As said in the subject, desktop decoration settings keeps resetting after rebooting. For me it is quite boring and annoying. Why it happens? Ubuntu should keeps my preferences (as in previous versions - my Ubu 10.10, Unity)

---

### Post by Copper Bezel on 2011-03-27
Is it related to the issue in [this](http://ubuntuforums.org/showthread.php?t=1575703) megathread, or is it something else? 

Do you mean the window decorations, specifically, as in the window frame (title bar and borders,) or is it the GTK skin as well? If you're using an Emerald decoration theme, you'll need to change your Compiz settings to use Emerald in place of Metacity settings for the window frame.

---

### Post by tpsa on 2011-03-28
Even in the window frame. The basic window frame set is very basic. Minimizing of windows does not work, switching windows does not work (after reboot, after switch to advanced decoration starts working...)

Gnome/Unity themes are working

---

### Post by Copper Bezel on 2011-03-28
It does sound more likely to be the Gnome Settings Daemon problem from the thread I linked, then. Does restarting Gnome Settings daemon (running in terminal, killall gnome-settings-daemon && gnome-settings-daemon) bring your preferences back to normal?

---

### Post by tpsa on 2011-03-31
Not exactly. It changes theme (but it seems for me not standard for gnome - completly grey), but it does not change window frame.

---

