---
title: "how do i make kde apps look better in jaunty"
date: 2009-06-21
forum: Desktop Environments
---

### Post by morganpatrick on 2009-06-21
so kcontrol appears to be gone, and meanwhile the new amarok looks terrible and i grabbed a kde based git gui which also looks terrible. is there a new control panel i can grab to make this look better in my (gnome based) ubuntu?

related question: is there a kde theme to make these apps just look like the standard jaunty human gnome theme?

---

### Post by konqueror7 on 2009-06-21
have you tried using "Qt Config" in the *System > Preferences*? there seems to be an option on how will you Qt-based applications (most KDE apps) look like.

---

### Post by morganpatrick on 2009-06-21
thanks for the tip. I just tried that and it didn't change the kde apps.

---

### Post by ad_267 on 2009-06-21
See [https://bugs.launchpad.net/ubuntu/+bug/349946](https://bugs.launchpad.net/ubuntu/+bug/349946) and [https://bugs.launchpad.net/ubuntu/+bug/346084](https://bugs.launchpad.net/ubuntu/+bug/346084)

I think qtconfig only works for pure qt apps, not kde applications. You can run this command to set your kde applications to use your gtk theme:

```
kwriteconfig --file kdeglobals --group General --key widgetStyle gtk
```

---

### Post by konqueror7 on 2009-06-21
> **ad_267 said:**
> See [https://bugs.launchpad.net/ubuntu/+bug/349946](https://bugs.launchpad.net/ubuntu/+bug/349946) and [https://bugs.launchpad.net/ubuntu/+bug/346084](https://bugs.launchpad.net/ubuntu/+bug/346084)

I think qtconfig only works for pure qt apps, not kde applications. You can run this command to set your kde applications to use your gtk theme:

kwriteconfig --file kdeglobals --group General --key widgetStyle gtk

that sucks...anyway, i read the bug report, and someone was able to find a temporary fix, [here]("https://bugs.launchpad.net/ubuntu/+bug/349946/comments/7").

---

### Post by morganpatrick on 2009-06-22
ok well i ran that command above and it appears to have done nothing, and i went and installed the packages as outlined in that bug page and i got a system settings app that has nothing in it. it's just a search bar that turns up nothing and a 'back to overview' button thats inactive and thats it.

---

### Post by ad_267 on 2009-06-22
> **morganpatrick said:**
> ok well i ran that command above and it appears to have done nothing, and i went and installed the packages as outlined in that bug page and i got a system settings app that has nothing in it. it's just a search bar that turns up nothing and a 'back to overview' button thats inactive and thats it.

Hmm that command works for me with digikam and k9copy. You probably have to log out and back in again for it to work.

---

### Post by morganpatrick on 2009-06-22
i'm just going to switch to kubuntu. all the kde stuff seems to do the **** gnome apps won't do for me anyway. amarok is unparalleled, as is quanta, basket note pads, and probably a mess of other stuff i dont even know about.

---

### Post by morganpatrick on 2009-06-22
ok now i'm in kubuntu and **** looks worse than ever. the interfaces in kubuntu are more multidimensional, make more sense, and look like **** on a shingle. what do i have to do to make this look tolerable????

---

### Post by morganpatrick on 2009-06-22
ok that sucked. now i'm back in normal ubuntu again. anybody out there??

---

### Post by Closed_Port on 2009-06-23
Here's how it worked for me:
Install systemsettings and kdebase-workspace. The second package will pull in quite a lot of stuff but I found that it is needed to get systemsettings to work. Without it, I encountered an empty systemsetting as you describe above.

Now you should be able to select gtk+ as your KDE style and change fonts and icons according to your needs.

---

### Post by morganpatrick on 2009-06-23
thanks~!

---

### Post by morganpatrick on 2009-09-18
ugh i installed all this stuff and rebooted and I still have a blank sytem settings window. This stinks.

---

### Post by morganpatrick on 2009-09-22
> You can run this command to set your kde applications to use your gtk theme:

```
kwriteconfig --file kdeglobals --group General --key widgetStyle gtk
```

This is the ONLY -- I repeat, the ONLY -- solution that actually works to address this problem. Everything else I've read on ubuntuforums.org or anywhere else on the web has turned out to be hogwash. Thank you for this!

This command will change the window style to be like the default gte style. I also did a fresh install and grabbed a bunch of kde4 apps with dependencies, plus systemsettings and kdeartwork and I have control over the style from system settings.

Now, as for kde3 apps: Should I add an old repo and install kcontrol? Do you have another one-liner that will get kde3 to use the right style? I changed my gtk and kde4 icons to tango, so maybe it's not that simple. Thanks for the help so far!

---

### Post by morganpatrick on 2009-09-23
For KDE3 [these instructions]("http://ubuntuforums.org/showthread.php?t=1012759") worked.

---

