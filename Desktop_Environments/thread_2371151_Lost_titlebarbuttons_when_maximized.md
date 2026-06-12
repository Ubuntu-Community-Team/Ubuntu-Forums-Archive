---
title: "Lost titlebar/buttons when maximized"
date: 2017-09-11
forum: Desktop Environments
---

### Post by accounts0 on 2017-09-11
After the most recent aptitude upgrade a day or so ago now I have this problem where if I maximize any window the only way to use the buttons on the titlebar is to right-click the taskbar entry & uncheck 'Maximize'. Not sure how to fix it.

Screenshots:
[https://imgur.com/a/MC2vF](https://imgur.com/a/MC2vF)

---

### Post by accounts0 on 2017-09-11
After tinkering for the last hour I've determined the problem lies in "Panel Options > Panel Settings > More Settings > Visibility Section" where now with the default setting of "Always Visible" is now allowing windows to be below the panel. eg. In the case of when a window is maximized, or also when the global window placement logic decides to align to the top of the desktop space which otherwise would be defined by the bottom of the top panel & isn't anymore.

I've applied a less-than-ideal workaround by selecting "Windows Can Cover" in "Panel Options > Panel Settings > More Settings > Visibility Section".

EDIT:
Also filed a bug report in case I'm not the only one:

[https://bugs.kde.org/show_bug.cgi?id=384604](https://bugs.kde.org/show_bug.cgi?id=384604)

---

