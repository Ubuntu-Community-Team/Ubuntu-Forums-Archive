---
title: "How to uninstall and then reinstall Terminal?"
date: 2009-05-27
forum: General Help
---

### Post by RafiB on 2009-05-27
Hi,
I have COMPLETELY wrecked my terminal...
Can someone tell me how to uninstall and then reinstall terminal, or if there is an easy and simple way to edit the terminal profiles from outside terminal?

What I did was edit the General profile to run custom code every time it runs. That code was to run a new terminal window, that is transparent and so on...now when I open terminal, it flashes for a moment in on one part of the screen, then closes and opens somewhere else. This happens about 5 times, and then it closes permanently.

Thanks,
Raf

---

### Post by noodles21 on 2009-05-27
not sure how to uninstall and reinstall...but when you open terminal, imediately hit CTRL C. that stops any running code, then you should be able to undo what you did in the General profile.

---

### Post by kpkeerthi on 2009-05-27
There should a config file somewhere in ~/.gnome2 or ~/.config where gnome terminal settings are stored. Deleting the file should restore the settings back to default.

I'm not in front of Ubuntu to check for you right now.

---

### Post by kpkeerthi on 2009-05-27
Press ALT + F2 and enter **gconf-editor**. Navigate to /apps/gnome-terminal/. Delete the corrupted profiles.

You can also check the folder ~/.gconf/apps/gnome-terminal/profiles/ in **nautilus**

---

