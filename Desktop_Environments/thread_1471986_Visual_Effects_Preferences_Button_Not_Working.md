---
title: "Visual Effects Preferences Button Not Working"
date: 2010-05-04
forum: Desktop Environments
---

### Post by darthpenguin on 2010-05-04
Hi All. I just installed Ubuntu 10.04. I added the simple-ccsm package through apt-get. I like the new option I now have under the Visual Effects tab in Appearance Preferences. I can now choose None, Normal, Extra, or Custom. The problem is when I click the "Preferences" button beside custom nothing happens. It should open simple-ccsm. In fact if I try to run simple-ccsm from the terminal I get this;

/usr/bin/simple-ccsm:40: DeprecationWarning: Use the new widget gtk.Tooltip
  Tooltips = gtk.Tooltips()
/usr/bin/simple-ccsm:182: DeprecationWarning: Use the new widget gtk.Tooltip
  Tooltips = gtk.Tooltips()
/usr/bin/simple-ccsm:545: DeprecationWarning: Use the new widget gtk.Tooltip
  Tooltips.set_tip(widget, _(("Can't find the animation plugin.")))
/usr/bin/simple-ccsm:415: DeprecationWarning: Use the new widget gtk.Tooltip
  Tooltips.set_tip(self, _("Disabled"))
Traceback (most recent call last):
  File "/usr/bin/simple-ccsm", line 515, in CheckAccessibility
    plugin = self.Context.Plugins[name]
KeyError: 'ezoom'
Traceback (most recent call last):
  File "/usr/bin/simple-ccsm", line 1374, in <module>
    mainWin = MainWin(context, page)
  File "/usr/bin/simple-ccsm", line 1170, in __init__
    self.Update()
  File "/usr/bin/simple-ccsm", line 1217, in Update
    self.ProfilePage.Update()
  File "/usr/bin/simple-ccsm", line 530, in Update
    self.CheckAccessibility()
  File "/usr/bin/simple-ccsm", line 515, in CheckAccessibility
    plugin = self.Context.Plugins[name]
KeyError: 'ezoom'

The regular compizconfig-settings-manager works fine and I actually prefer it. So my question is; can I bind the "Preferences" button to open ccsm instead of simple-ccsm? If not, how can I fix the simple-ccsm package?

Thanks

---

### Post by darthpenguin on 2010-05-04
Okaaaaaaaaaayyyyyyyyyyy..... weird. I don't know what I did but simple-ccsm is working now. But I'd still like the preferences button to open ccsm (not simple-ccsm) anyway to do this? thanks.

---

### Post by TJSL on 2010-09-28
[IMG]file:///tmp/moz-screenshot.png[/IMG]I had the same problem.  It went away after I installed a couple more compiz packages (not exactly sure which ones).  The attached image shows all of the compiz packages that I have installed.  Compare these against the ones that you have installed to narrow down which package is causing the issue.

---

