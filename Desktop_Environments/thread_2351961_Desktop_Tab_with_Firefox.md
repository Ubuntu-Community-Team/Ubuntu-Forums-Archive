---
title: "Desktop Tab with Firefox"
date: 2017-02-08
forum: Desktop Environments
---

### Post by angel mike on 2017-02-08
I did a general update of the apps using the Synaptic tool to cure a vanishing 'Ubuntu Software' every time I tried to open it from the launcher. That worked but now every time I try to open a new tab with Firefox I get 'chrome://desktop/content/desktop.htm' plus a comment below saying 'right click in this tab to add content to the desktop'.

How do I get back to just a plain tab ? As far as I know Chrome is not on my system anyway.

---

### Post by howefield on 2017-02-08
If all else fails, removing or renaming the ~/.mozilla folder will restart Firefox with a fresh profile.

Do you have any addons installed, eg something like Chrome Cast ?

---

### Post by angel mike on 2017-02-08
Thanks howefield will try that.
Yes I did download  the Addons program to get a way of adding web page links to the desktop but it said it did not work with the current version of Firefox.
Anyway I used the bookmark method and drag/dropped onto the desktop. Is there a way to check the addons ?

---

### Post by angel mike on 2017-02-08
I uninstalled Firefox and re-installed it but did not solve the problem.

---

### Post by howefield on 2017-02-08
> **angel mike said:**
> Thanks howefield will try that.
Yes I did download  the Addons program to get a way of adding web page links to the desktop but it said it did not work with the current version of Firefox.
Anyway I used the bookmark method and drag/dropped onto the desktop. Is there a way to check the addons ?

Not sure what you mean by check the add-ons ?

When Firefox is updated it generally runs a check on your add-ons on the first launch after the update to check compatibility with your add-ons, if there is an issue you have a choice of checking for an update to the add-on or disabling it.

Sounds like you just need to uninstall the problematic add-on.

---

### Post by howefield on 2017-02-08
> **angel mike said:**
> I uninstalled Firefox and re-installed it but did not solve the problem.

Uninstalling by itself won't do anything as it will leave the profile located in your ~/.mozilla folder. Removing or renaming that folder is what you need.

---

### Post by ajgreeny on 2017-02-08
Go to the help menu in FF and choose "Restart with Add-ons Disabled"; that will show you if there is a problem with your add-ons.

---

### Post by angel mike on 2017-02-08
Thanks to howefield and ajgreeny and will pursue the advice. This might be a dumb question but where is the help menu in FF? I click on the menu tab but see no help icon !

---

### Post by howefield on 2017-02-08
> **angel mike said:**
>  This might be a dumb question but where is the help menu in FF? I click on the menu tab but see no help icon !

Unity desktop environment ?

Mouse over on the top panel and the menus should appear.. if not try Alt + F keys.

Or from the hamburger menu, click on the question mark icon.

---

### Post by angel mike on 2017-02-08
Thanks howefield for the hamburger menu option - I found the question mark. Will start the investigation !

---

### Post by angel mike on 2017-02-08
Great - I did as you suggested aigreeny and disabled the addons and refreshed FF - and I now have my normal setup. Thank you both !!

---

