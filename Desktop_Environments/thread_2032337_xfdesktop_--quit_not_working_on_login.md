---
title: "xfdesktop --quit not working on login"
date: 2012-07-23
forum: Desktop Environments
---

### Post by vectorthorn on 2012-07-23
i know that issuing "xfdesktop --quit" will kill xfdesktop so that compiz-wallpaper can do its thing, but adding that command to startup apps doesn't do anything.

i also seen in another thread that you can comment it out near line 280 in the file **/etc/xdg/xfce4/xinitrc**, but, again, that is not persistent.

does any one know how to make this change persistent, so that you don't have to issue the command from the terminal every time you log in?

TIA

---

### Post by Toz on 2012-07-23
I haven't actually tried this, but it should work. Go to Settings Manager -> Session and Startup -> Session tab. Quit the xfdesktop program and then save the session.

Or you could uninstall xfdesktop4. It seems to only remove the xubuntu-desktop meta package along with it.

---

### Post by vectorthorn on 2012-07-23
perhaps this is a bit of a noob question, but don't i want to KEEP xubuntu-desktop?

===edit===
nevermind, did read the package info when i first started to try this. just read the package info, and it seems that it is safe to remove. will try that and let you know. thanks.

---

