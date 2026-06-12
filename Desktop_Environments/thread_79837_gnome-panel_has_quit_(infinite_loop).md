---
title: "gnome-panel has quit (infinite loop)"
date: 2005-10-20
forum: Desktop Environments
---

### Post by HankB on 2005-10-20
I just upgraded from 5.04 to 5.10 (AMD64, but it may not be a 64 bit problem.)

I can login using a gnome desktop, but my wife's login is not useful. She gets a popup 'The Application "gnome-panel" has quit unexpectedly.' Of course if you close or restart, it does the sme thing ad nauseum. I even tried the failsafe login and it did the same thing. The only way to break out of the loop is with <ctrl><alt><bkspce>

There is also a popup that comes up first that says "I've detected a panel already running and will now exit."

I tried renaming her .gnome2 directory and met with the same result.

How can I determine what's doing this? Is there some way to recover by deleting or renaming configuration files?

thanks,
hank

---

### Post by aysiu on 2005-10-20
I'd try a few things. First, while your wife is logged in, control-alt-F1. This should change to the console version of her login. Within that, type ```
killall gnome-panel
```. Then, control-alt-F7. Any difference?

If that doesn't work, while you're logged in as you, launch this command ```
gksudo nautilus
```. Then, copy your wife's important config files (for example, if she uses Firefox and Thunderbird, I'd copy /home/wifesusername/.mozilla and /home/wifesusername/.mozilla-thunderbird). Add a new account for her and copy the config files to the new account.

---

