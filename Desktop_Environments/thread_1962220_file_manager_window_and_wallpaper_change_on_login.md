---
title: "file manager window and wallpaper change on login"
date: 2012-04-20
forum: Desktop Environments
---

### Post by DanBender on 2012-04-20
I'm setting up Qimo-session on a laptop for my young son, and am experiencing some unexpected behavior on startup of his session. The session seems to start just fine, with the panels I've set up coming up and the Qimo wallpaper...and then, suddenly, a Nautilus window opens at his home directory (isn't Thunar the default FM in xfce?), and the wallpaper turns to that purple Ubuntu wallpaper. I don't want the wallpaper since I want things to be bright and cartoony for him, and I don't need Nautilus opening since I don't want him to be messing around with files yet.

There doesn't seem to be an obvious reason why it's doing this, at least not from within Qimo. The Nautilus preferences don't seem to mention anything about startup behavior. The file ./config/autostart/xfce4-settings-helper-autostart is empty, so that's not calling anything. Any suggestions for what I should check?

Thanks for the help.

---

### Post by DanBender on 2012-04-27
After some poking around, I believe it is something like what is being described in [this thread.]("http://ubuntuforums.org/showthread.php?t=785210") I deleted everything in the .cache folder, and the next login it didn't pop up with a Nautilus window (still changed the wallpaper though).

Unfortunately, the login after that it went right back to doing it again. I believe what is being described in post #9 or #10 needs to happen, but it's unclear how I can accomplish it now. Since Ubuntu isn't using Gnome anymore, the settings manager he's talking about doesn't exist, and there isn't a .config/gdm for "gnome desktop" config files either. Any ideas?

---

### Post by DanBender on 2012-05-01
In the XFCE Settings Manager, there is a checkbox for "Launch GNOME services on startup" or something like that. Unchecking it seems to have solved the problem for me. Although I don't know what else it turned off, since it is awfully non-specific.

---

