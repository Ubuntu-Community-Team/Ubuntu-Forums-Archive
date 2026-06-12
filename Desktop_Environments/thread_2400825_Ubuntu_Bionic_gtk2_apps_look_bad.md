---
title: "Ubuntu Bionic: gtk2 apps look bad"
date: 2018-09-10
forum: Desktop Environments
---

### Post by manmath on 2018-09-10
On my Ubuntu Bionic, gtk2 apps look really ugly. Have a look at the screenshot (attached) where nautilus looks fine, whereas artha (gtk2) looks ugly. Please suggest me a fix.
[ATTACH=CONFIG]281041[/ATTACH]

---

### Post by Frogs Hair on 2018-09-10
I can't reproduce the effect . I don't think you would be missing any gtk2 or 3 theme engines on 18.04 which is all I find related to this issue on the web so far. Using Ambiance theme.

---

### Post by again? on 2018-09-10
I use xubuntu but booting to a live cd of Ubuntu 18.04 and installing artha it does not look like your pic.
**Edit:** Frogs Hair confirms that it is most likely some change you have made.

Are you using the default theme?
Try a different user account to check you have not set some user config.

---

### Post by Dennis N on 2018-09-10
Some gtk2 applications may require a specific theme engine installed to look right with certain gtk2 themes.  Look for packages matching **gtk2-engines*** There are several.
(In Ubuntu 18.04, only two are installed by default. **gtk2-engines-murrine** and **gtk2-engines-pixbuf**)

---

### Post by manmath on 2018-09-15
Thank you all for coming to my rescue. The issue has been resolved. I'm sorry for not replying on time. Actually the issue was very trivial. While customizing the theme I had somehow disabled "Gnome Settings Daemon's xsettings plugin." After I enabled the same and rebooted the system it all back to normal.

---

